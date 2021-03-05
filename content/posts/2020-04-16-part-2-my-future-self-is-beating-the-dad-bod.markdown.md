---
author: kylepott
date: 2020-04-16 01:56:24+00:00
draft: false
title: 'Part 2: My Future Self is Beating the Dad-Bod'
type: post
url: /2020/04/16/part-2-my-future-self-is-beating-the-dad-bod/
categories:
- data science
tags:
- python
- Selenium
- trendweight
---


![](https://technicalagain.com/wp-content/uploads/2020/04/Screenshot-from-2020-04-15-20-46-13.png)






Every day right at 4pm when I should just about be getting hungry for dinner and losing motivation, I get a text message from **My Future Self**.  The text message reminds me of my weight for today and compares it against all of the other 1048 entries I've logged on my scale the last decade.







**My Future Self **is smart enough to compare my weight to the previous day to give some encouragement or tough love.  It tracks my distance to goal, too.  The percentile is also dynamic so it will always be accurate even when more entries are added.  Lastly, My Future Self keeps my a journal of my daily weight reading in a nice and tidy Excel spreadsheet.







This is part 2 [to my previous post](https://technicalagain.com/2020/04/14/according-to-facebook-i-will-have-a-dad-bod-on-june-28-2021/).  Reading part 1 will help you to understand what I'm talking about here a little bit better. In part 1 I said: _I am planning to tinker with the Withings API and try to create a more real-time “scorecard” to know what percentile I’m in and if I’m delaying (and ultimately defeating) the Dad-Bod date._







I did tinker with the Withings API and I thought it was painful.  So I went down another path.  I wrote a screen scraper in Python using the Selenium library to get my current weight from [TrendWeight](https://trendweight.com/dashboard/). I then add the weight to my weight journal, and send myself a text message.  My Future Self runs as a cron job on a free-tier EC2 instance and uses the Amazon Simple Email Service (SES) to send the email. 







I will eventually add it to my GitHub repo, but here is all the code for My Future Self (warning, it's ugly, not refactored) if you'd like to meet your future self, too.







Here's to defeating the Dad-Bod!






    
    <code>import requests
    import urllib.request
    import time
    from bs4 import BeautifulSoup
    from selenium import webdriver
    from pyvirtualdisplay import Display
    import datetime
    from datetime import date
    import pandas as pd
    import pandas as pd2
    from datetime import datetime
    
    # headless
    display = Display(visible=0,size=(800, 600))
    display.start()
    
    #run pkill chrome to cleanup the process from the shell
    browser = webdriver.Chrome()
    
    browser.get("https://trendweight.com/u/91a151bdce4143/")
    #take a breathe allowing JavaScript to load
    time.sleep(2)
    soup = BeautifulSoup(browser.page_source, "html.parser")
    
    todays_weight = soup.findAll('td', attrs={'class':'measuredWeight'})[0].string
    weight_today = float(todays_weight)
    
    todayz_date = str(date.today())
    
    #open master spreadsheet and append today's weight to the bottom.
    df = pd.read_excel("ThreeCleanSheets.xlsx")
    df2 = pd.DataFrame({"weigh_in_date":[todayz_date], "weight":[weight_today]}) 
    df = df.append(df2)
    
    #more cleanup to remove dups
    df.drop_duplicates(inplace=True)
    
    #Save the updated sheet.
    df.to_excel('ThreeCleanSheets.xlsx',index=False)
    df3 = pd2.read_excel("ThreeCleanSheets.xlsx")
    
    df3['Percentile_rank']=df3.weight.rank(pct=True)
    
    #establish the index for our new weight
    x = (len(df3))-1
    
    #send the email logic is next
    
    import boto3
    from botocore.exceptions import ClientError
    
    # Replace sender@example.com with your "From" address.
    # This address must be verified with Amazon SES.
    SENDER = "My Future Self <kylepott@gmail.com>"
    
    # Replace recipient@example.com with a "To" address. If your account 
    # is still in the sandbox, this address must be verified.
    RECIPIENT = "kylepott@gmail.com"
    
    # Specify a configuration set. If you do not want to use a configuration
    # set, comment the following variable, and the 
    # ConfigurationSetName=CONFIGURATION_SET argument below.
    #CONFIGURATION_SET = "ConfigSet"
    
    # If necessary, replace us-west-2 with the AWS Region you're using for Amazon SES.
    AWS_REGION = "us-east-1"
    
    # The subject line for the email.
    SUBJECT = ""
    
    # The email body for recipients with non-HTML email clients.
    BODY_TEXT = ""
    
    weight_up_or_down = df3.weight[int(x)] - df3.weight[int(x) -1]
    
    #173 is my goal
    how_much_to_go = df3.weight[int(x)] - 173.
    # The HTML body of the email.
    if weight_up_or_down < 0:
        enouragement = " Way to go, your weight is less than yesterday by " + str(round((weight_up_or_down),2)) + " pounds."
    else:
        enouragement = " Get back at it, you can do it! Your weight was not less than yesterday. You went up" + str(round((weight_up_or_down),2))
    
    BODY_HTML = "<html><head></head><body><p>Today you weigh " + str(round((df3.weight[int(x)]),2)) + " which is in the " + str(round((df3.Percentile_rank[int(x)]),2)) + " percentile." + enouragement + " Keep going! Only " + str(round((how_much_to_go),2)) + " pounds left to go to your goal!</p></body></html>"
    
    # The character encoding for the email.
    CHARSET = "UTF-8"
    
    # Create a new SES resource and specify a region.
    client = boto3.client('ses',region_name=AWS_REGION)
    
    # Try to send the email.
    try:
        #Provide the contents of the email.
        response = client.send_email(
            Destination={
                'ToAddresses': [
                    RECIPIENT,
                ],
            },
            Message={
                'Body': {
                    'Html': {
                        'Charset': CHARSET,
                        'Data': BODY_HTML,
                    },
                    'Text': {
                        'Charset': CHARSET,
                        'Data': BODY_TEXT,
                    },
                },
                'Subject': {
                    'Charset': CHARSET,
                    'Data': SUBJECT,
                },
            },
            Source=SENDER,
            # If you are not using a configuration set, comment or delete the
            # following line
            #ConfigurationSetName=CONFIGURATION_SET,
        )
    # Display an error if something goes wrong.	
    except ClientError as e:
        print(e.response['Error']['Message'])
    else:
        print("Email sent! Message ID:"),
        print(response['MessageId'])
    </code>










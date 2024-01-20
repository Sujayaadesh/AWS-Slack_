
# AWS_slack



## Introduction:


Designing an Automatic Data Collection and Storage System with AWS Lambda and Slack Integration for Server Availability Monitoring and Slack Notification using AWS Lambda, CloudWatch, Slack API.


## Tools:
    Language - Python
    Libraries - psycopg2
    AWS services - AWS Lambda, CloudWatch, AWS SNS, AWS RDS
    Slack - Slack API, Slack workspac



## Process:



**Lambda_1:** 


     1.Create a Lambda function that fetches data from the specified API and inserts it into a PostgreSQL database.
     2.Download and include the required packages (requests and psycopg2) in the Lambda layer.
     3.Handle the API request, extract relevant data, and establish a connection to the PostgreSQL database.
     4.Insert the retrieved data into the "slack_data" table.
     5.Return a success response if the server status is True, otherwise raise an exception.


**Lambda_2:**
   
    1.Create a Lambda function that sends server error notifications to a Slack channel using a webhook.
    2.Prepare a Slack message and send it to the specified webhook URL.
    3.Handle possible HTTP and server connection errors and print corresponding messages.

**SNS Topic:**

    Create an SNS topic that triggers Lambda-2 for Slack notifications.

**CloudWatch Alarm:**

    1.Create a CloudWatch alarm that triggers based on Lambda-1 failure.
    2.Select the appropriate Lambda metric and set the threshold value.
    3.Add the SNS topic to the alarm configuration.
    
**Testing:**

    1.Manually modify the code in Lambda-1 to simulate a server failure.
    2.The failure triggers the CloudWatch alarm, which in turn triggers Lambda-2 to send a Slack notification.

# AWS-Slack_
Designing an Automatic Data Collection and Storage System with AWS Lambda and Slack Integration for Server Availability Monitoring and Slack Notification using AWS Lambda, CloudWatch, Slack API.
AWS-slack-project
Designing an Automatic Data Collection and Storage System with AWS Lambda and Slack Integration for Server Availability Monitoring and Slack Notification using AWS Lambda, CloudWatch, Slack API.

Technology
Language - Python
Libraries - psycopg2
AWS services - AWS Lambda, CloudWatch, AWS SNS, AWS RDS
Slack - Slack API, Slack workspace
Workflow
Lambda-1:

Create a Lambda function that fetches data from the specified API and inserts it into a PostgreSQL database.
Download and include the required packages (requests and psycopg2) in the Lambda layer.
Handle the API request, extract relevant data, and establish a connection to the PostgreSQL database.
Insert the retrieved data into the "slack_data" table.
Return a success response if the server status is True, otherwise raise an exception.
Lambda-2:

Create a Lambda function that sends server error notifications to a Slack channel using a webhook.
Prepare a Slack message and send it to the specified webhook URL.
Handle possible HTTP and server connection errors and print corresponding messages.
SNS Topic:

Create an SNS topic that triggers Lambda-2 for Slack notifications.

CloudWatch Alarm:

Create a CloudWatch alarm that triggers based on Lambda-1 failure.
Select the appropriate Lambda metric and set the threshold value.
Add the SNS topic to the alarm configuration.
Testing:

Manually modify the code in Lambda-1 to simulate a server failure.
The failure triggers the CloudWatch alarm, which in turn triggers Lambda-2 to send a Slack notification.

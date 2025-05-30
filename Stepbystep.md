Step 1: Create a CloudWatch Alarm for EC2 CPU Usage (10 mins)

1. Go to your EC2 instance:

    Open AWS Console

    Navigate to EC2 > Instances

    Click on your running EC2 instance


2. Create the alarm:

    In the Monitoring tab, click Create alarm

    Under “Specify metric and conditions”:

        Metric: CPUUtilization

        Statistic: Average

        Period: 5 minutes

        Threshold: Greater than 70%

    Click Next

Step 2: Set Up Amazon SNS (for Email Notifications) (10 mins)

1. Go to SNS:

    In the AWS Console, go to Simple Notification Service (SNS)

2. Create a Topic:

    Click Topics > Create topic

    Choose Standard

    Name: EC2-Alerts

    Click Create topic

3. Create a Subscription:

    On your new topic page, click Create subscription

        Protocol: Email

        Endpoint: your email address

    Click Create subscription

    Check your email and confirm the subscription (important!, i have some trouble latter because i forgot this)

Step 3: Connect Alarm to SNS Topic (10 mins)

1. Go back to your CloudWatch alarm setup:

    On the Add notification section:

        Select Send a notification to → Your SNS topic (EC2-Alerts)

    Click Next, review, and then Create Alarm

2. Test the alert (Optional):

    You can manually simulate high CPU by SSH-ing into EC2 and running:

sudo apt update
sudo apt install stress -y
stress --cpu 2 --timeout 60

    Wait ~5-10 mins for alarm to trigger

    Watch for the email alert!

and if you need more stressing you can try this 
sudo apt install stress-ng

Then run with higher CPU load:

stress-ng --cpu 2 --cpu-load 90 --timeout 300

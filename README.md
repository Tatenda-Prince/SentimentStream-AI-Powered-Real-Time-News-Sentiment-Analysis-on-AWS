# AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS

## Technical Architecture


![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/2a20d4135523e8a2043be772779df615e5b71a0d/screanshots/Screenshot%202025-03-05%20180518.png)


## Project Overview

SentimentStream is a cloud-native, AI-powered system that fetches real-time news, analyzes sentiment using AWS Comprehend, and stores insights in Amazon DynamoDB. It enables businesses to track sentiment trends efficiently, making data-driven decisions based on news insights.The project is fully automated with Terraform, following best practices in Infrastructure as Code (IaC), ensuring easy deployment and scalability.

## Project Objective

This project solves the challenge of real-time news sentiment tracking by automating:

1.News Fetching – Retrieve real-time news articles from NewsAPI.

3.Sentiment Analysis – Use AWS Comprehend to classify articles as Positive, Negative, Neutral, or Mixed.

4.Data Storage & Querying – Store results in DynamoDB for quick sentiment insights.

Why It Matters? Businesses need real-time insights on market trends, competitor analysis, and crisis detection. SentimentStream helps them stay ahead by providing AI-driven sentiment intelligence.

## Features

1.Fully Serverless Architecture – Uses AWS Lambda, S3, DynamoDB, and Comprehend.

2.Real-Time News Fetching – Automatically retrieves news from NewsAPI.

3.AI-Powered Sentiment Analysis – Uses AWS Comprehend for accurate sentiment classification.

4.Fast Sentiment Queries – Stores results in DynamoDB for instant lookups.

5.Scalable & Cost-Efficient – Serverless and pay-as-you-go AWS model.

6.Terraform-Powered Deployment – Easily provision AWS infrastructure with Infrastructure as Code (IaC).

## Technologies Used

1.AWS Lambda – Serverless compute for news fetching, querying sentiments & sentiment analysis

1.Amazon S3 – Stores raw news articles.

3.AWS Comprehend – AI-based sentiment analysis.

4.Amazon DynamoDB – NoSQL database for fast sentiment lookups.

4.Terraform – Infrastructure as Code for automated AWS provisioning.


## Use Case

A financial investing firm uses the AI-Powered News Sentiment Analysis System to monitor sentiment trends in real time.  By analysing news stories about stock markets, industries, and firms, the firm learns about public perception and market mood.  If news opinion towards a given company shifts unfavourable, the corporation can immediately modify its investing strategy to reduce risk.  In contrast, positive mood trends may indicate possible prospects for growth.  This automated technology enables traders and analysts to make data-driven investment decisions, decreasing human work and improving strategic decision-making.


## Prerequisites

1.https://newsapi.org/: register and get your API

2.AWS Account with configured Access key and Secret access key.

3.Terraform & AWS CLI installed (if using Terraform for infrastructure)


## Step 1: Clone the Repository

1.1.Clone this repository to your local machine.

```language
git clone https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS.git
```


## Step 2 : Run Terraform workflow to initialize, validate, plan then apply

2.1.Terraform will create:
AWS Lambda functions (News Fetching, Sentiment Analysis, Querying)
Amazon S3 bucket (for storing news articles)
AWS Comprehend integration (for sentiment analysis)
Amazon DynamoDB table (for sentiment storage & queries)

2.2.In your local terraform visual code environment terminal, to initialize the necessary providers, execute the following command in your environment terminal.

```Language
terraform init
```

Upon completion of the initialization process, a successful prompt will be displayed, as shown below.


![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/29cc005d698bea6c1a3f81afdf6b165dd11e2b65/screanshots/Screenshot%202025-03-05%20182529.png)



2.3.Next, let’s ensure that our code does not contain any syntax errors by running the following command

```Language
terraform validate
```

The command should generate a success message, confirming that it is valid, as demonstrated below.


![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/0de5c67f631048ba65f3dae74481c2ac58fc4597/screanshots/Screenshot%202025-03-05%20182609.png)


2.4.Let’s now execute the following command to generate a list of all the modifications that Terraform will apply.

```Language
terraform plan
```

![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/40ba333622d12ff143a80b986a208b9896fa02b4/screanshots/Screenshot%202025-03-05%20182737.png)

The list of changes that Terraform is anticipated to apply to the infrastructure resources should be displayed. The “+” sign indicates what will be added, while the “-” sign indicates what will be removed.


2.5.Now, let’s deploy this infrastructure! Execute the following command to apply the changes and deploy the resources. Note — Make sure to type “yes” to agree to the changes after running this command.


```Language
terraform apply
```

Terraform will initiate the process of applying all the changes to the infrastructure. Kindly wait for a few seconds for the deployment process to complete.

![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/705b649102158af17a5909896bd66590f92d3a05/screanshots/Screenshot%202025-03-05%20182948.png)


## Success

The process should now conclude with a message indicating “Apply complete”, stating the total number of added, modified, and destroyed resources, accompanied by several resources.


![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/e91a2277aab51edd3c892d84e6a5178337b85ae6/screanshots/Screenshot%202025-03-05%20183024.png)



## Step 3: Verify creation of our resources

3.1.In the AWS Management Console, head to the Amazon S3 dashboard and verify that a S3 bucket was successfully created as shown below 

![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/a04b5fd5e5958ec4f1d01e5ee487e4f12ec17b8d/screanshots/Screenshot%202025-03-05%20183627.png)



3.2.In the AWS Management Console, head to the AWS Lambda dashboard and verify that you three lambda function that were successfully created.


![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/ff7334d02dce49b196bcf453933f0ae799370578/screanshots/Screenshot%202025-03-05%20183704.png)


3.3.In the AWS Management Console, head to the Amazon DynamoDB dashboard and verify that a table was successfully created as shown below

![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/69ff84f6dc036ac41fa67fc2a56e83b840c45b1d/screanshots/Screenshot%202025-03-05%20183728.png)


Now that all our resources we will move on to step 4, testing part invoking lambda function to fetch news articles from the external API and store the result in our S3 bucket.



## Step 4: Testing the System


4.1.Fetch News Articles

Manually trigger the `fetch_news` to fetch the articles form the external API.NOTE Use the AWS CLI.

```langauge
aws lambda invoke --function-name fetch_news --payload '{"timestamp": "20250305"}'  response.json

cat response.json
```

![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/21bb672be4e2db638f789873b9831cc651a03bfc/screanshots/Screenshot%202025-03-05%20140408.png)


Now verify if the news articles json fiel is successfully stored in the S3 bucket as shown below-


![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/ea68c007a97c6b9d1b951bf51eb147665785ce26/screanshots/Screenshot%202025-03-05%20140759.png)



Now download the news articles json file to your local machine.


![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/ceb5963fc89953627a312cd3d0629b9728dc5038/screanshots/Screenshot%202025-03-05%20140854.png)



4.2.Analyze Sentiment

Manually trigger the sentiment analysis Lambda in order for amazon comprehend to run analysis on the article stores in Amazon S3 and store the results in DynamoDB.

```langauge
aws lambda invoke --function-name analyze_sentiment --payload '{"file_key": "news_20250305.json"}' response.json

cat response.json
```

![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/502a1be4b1d0c6af6420799ca53550ab86a6cb83/screanshots/Screenshot%202025-03-05%20141404.png)


In AWS Managemaent Console, head to DynamoDB under tables click the `NewsSentiment` tables on the right hand panel click on `Explore items` the results should be as shown below-


![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/7e26eece47718fd75305e92e75ebc649751bc97d/screanshots/Screenshot%202025-03-05%20142011.png)




![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/92187710321f95c5d68df7e4fcea41d99aec5ee9/screanshots/Screenshot%202025-03-05%20142046.png)



Now that that the news article were successfully analyzed and store in DynamoDB for fast lookup, Now lets Query Sentiment Trends



4.3.Query Sentiment Trends

Now lets retrieve sentiment trends from DynamoDB for fast lookup.

1.First We will that query the `NEGATIVE` sentiment


```langauge
aws lambda invoke --function-name query_sentiment --payload '{"sentiment": "NEGATIVE", "keyword": "China"}' response.json

cat response.json | jq '.body | fromjson'
```



![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/ec413be3c7ca354676b91772da66492c19467baf/screanshots/Screenshot%202025-03-05%20143722.png)



2.Second We will that query the `POSITVE` sentiment

```langauge
aws lambda invoke --function-name query_sentiment --payload '{"sentiment": "POSITIVE", "keyword": "China"}' response.json

cat response.json | jq '.body | fromjson'
```



![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/5214409a68997b32b1bdeed7214749013ebeee5f/screanshots/Screenshot%202025-03-05%20144238.png)



3.Third we will query the `NUETRAL` sentiment


```langauge
aws lambda invoke --function-name query_sentiment --payload '{"sentiment": "NUETRAL", "keyword": "MacBook Air"}' response.json

cat response.json | jq '.body | fromjson'
```


![image_alt](https://github.com/Tatenda-Prince/AI-Powered-Real-Time-News-Sentiment-Analysis-on-AWS/blob/35841f4602f4e3e8f5a36e7ba015fa90b7ce2869/screanshots/Screenshot%202025-03-05%20144900.png)



## Future Enhancements

1.Multi-Source News Integration – Extend support beyond NewsAPI (e.g., Twitter, RSS feeds).

2.Time Event Triggering – Implement AWS EventBridge to automatically trigger alerts on sentiment spikes.

3.Visualization Dashboard – Use Amazon QuickSight or Grafana to create sentiment trend dashboards.



## Congratulations

We have succesfully created a fully serverless AI-driven system using AWS services like Lambda, S3, Comprehend, and DynamoDB.
Implementing Terraform for Infrastructure as Code (IaC), making deployment seamless and scalable.
Managing real-time data ingestion and processing, critical for businesses that rely on timely insights.
Creating a queryable sentiment analysis system, allowing users to extract meaningful trends.












































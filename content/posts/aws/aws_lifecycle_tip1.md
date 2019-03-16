---
title: "AWS LifeCycle Management - CloudWatch Logs Retention"
date: 2019-02-16T14:47:49+05:30
draft: true
toc: true
images:
tags: 
  - aws
  - lifecycle
---

Introduction
------------

The AWS Cloud Ecosystem has been growing at an impressive pace. Lots of new services have been launched over the past few years and many more will soon come. I have explored most of them and have been using it quite extensively . At the beginning , things look simple , you start with few services (typically S3,EC2 and Lambda) and then you slowly add other relevant ones. In just few months you would end up with lot of files in S3 , applications running in EC2 and Lambda and bunch of other things. 

At some point , your AWS Environment would have grown to a point , where things become too dense , your S3 Buckets will be having too much of data sitting , Cloudwatch Logs would have grown so much and the most important point , your AWS Costs will be spiralling upwards. Things soon become difficult to manage and then you would end up spending valuable time cleaning up the environment , removing unused services and files. 

So how do you ensure that your cloud environment is clean from the beginning ? What are the possible ways to do this ? 

In this post as well as forthcoming ones , I share the lessons that I learnt and how it has slowly helped in keeping the AWS Environment as clean as possible with minimal human involvement. 

CloudWatch Logs Retention Policy
--------------------------------

One of the things that I learnt was that for every Lambda that you setup , AWS automatically generates Cloudwatch Logs. These logs do not expire meaning they persist lifelong , which as time passes costs . 

So the first thing is to setup a Retention Policy for the Log. Once set , AWS will start removing the logs after they become expired , thereby reducing the cost of storing them . These also keeps the logs manageable in case of debugging. 

#### How do you set them up ? 

The simplest way is to use awscli command as shown below : 

```bash
   
   aws logs put-retention-policy --log-group-name [log_group_name] --retention-in-days [no_of_days]

   --log-group-name    : Name of the Log Group 
   --retention-in-days : The number of days to retain the log events in the specified log group. 
           Possible values are: 1, 3, 5, 7, 14, 30, 60, 90, 120, 150, 180, 365, 400, 545, 731, 1827, and 3653. 
   
```

In the forthcoming posts , I will list other ways that can be used to manage your cloud environment efficiently. 



---
title: "AWS LifeCycle Management - Managing Docker Images"
date: 2019-03-17
draft: false
toc: true
images:
tags: 
  - aws
  - lifecycle
---

Introduction
------------

In the [previous post]( {{< ref "posts/aws/aws_lifecycle_tip1.md" >}}) , I began with setting up the retention policies for Cloudwatch Logs. Once that was setup , I began exploring other resources that can be managed. One of the services that I most frequently started to use is AWS Batch . AWS Batch allows you to run batch workloads in AWS Cloud. 

AWS Batch is a service where you submit a job or array of jobs and the service takes care of the resource requirements . The job typically is a Docker image which is either stored in the Docker Repository or in AWS ECR(Elastic Container Repository). 

The way AWS ECR works is as follows :   
- You first create a new repository 
- You then start pushing the Docker image to it . 

So based on the requirements :  
+ You end up having multiple repositories
+ You end up with multiple versions of images.
+ By default most recently pushed image is tagged as latest.
+ Other versions become untagged . 
+ Every image takes up space and money 

Thus we will end up with a repository with 1 tagged and atleast 1 untagged images. 

### Questions : 
1. How do we ensure that the repository does not contain too many versions of the image ? 
2. How do we restrict it to say max of 2 or 3 versions of a Docker Image ? 

As it turns out , AWS provides a way for this , by means of setting up a Lifecycle Policy when creating a Repository.

ECR LifeCycle Policy 
--------------------

The lifecycle policies enable you to specify the lifecycle management of images in a repository. Basically its a set of rules that defines what actions to be taken on the images. This allows for cleaning up unused images . 

I won't get into the details of the policies. The [AWS Documentation](https://docs.aws.amazon.com/AmazonECR/latest/userguide/lifecycle_policy_examples.html) is good enough .

For my projects , I use the below policy which serves its purpose and helps in keeping the repositories update and clean.

```json
   {
    "rules": [
        {
            "rulePriority": 1,
            "description": "Keep only one untagged image, expire all others",
            "selection": {
                "tagStatus": "untagged",
                "countType": "imageCountMoreThan",
                "countNumber": 1
            },
            "action": {
                "type": "expire"
            }
        }
    ]
}
```

Basically , the above policy ensures that there is only 1 untagged image at all times. 

In the 2 posts written so far , I had to manually run the commands whenever I create a new repository or a lambda function . 

In the next post , I come up with a way to automate this management . Till then , I hope you have found the article useful.


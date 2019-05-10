---
title: "Setting up Postgres"
date: 2019-04-19
draft: false
toc: true
images:
tags:
 - postgres
 - database
---

Introduction
------------

Postgres has been my goto database for some time now and everytime , I go about setting up the database locally , I invariably find myself stuck in the below situations :  

1. Forgotten the Localhost Password and Username 
2. Unable to access the Database remotely . 
3. Creating roles and permissions. 

Then googling to fix these issues , led me to a variety of ways , predominantly in StackOverflow , where they suggest you to change postgresql.conf and few other configuration files. All these seemed little risky , given that you are trying to modify system level configurations without understanding the ramifications of the same. 

After a bit of more research , I came across an article posted in the DigitalOcean Community , which I found to be really good , well written and more importantly explained the steps involved. 

Thought it would be wise to keep a note of it , lest I encounter this situation again in future. 

So below are the links to them and I hope its useful . 

- Setting up Postgres : [Link](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04)

- Roles and Permission : [Link](https://www.digitalocean.com/community/tutorials/how-to-use-roles-and-manage-grant-permissions-in-postgresql-on-a-vps--2)

The best part is that the above articles does not require you to manipulate any of the default configuration files. 


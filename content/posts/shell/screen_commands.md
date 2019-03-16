---
title: "Commonly Used Screen Commands"
date: 2019-02-09T18:54:11+05:30
draft: false
toc: false
images:
tags: 
  - shell
  - screen
---

Introduction
------------

I have been using AWS for the past 2 years and its been incredible. There is just too many services in the AWS Ecosystem , but the most widely used are the EC2 Instances. In the beginning , I often faced frequent disconnections when I am connected to an EC2 Instance. As a result , the applications that were running in the instance get terminated and I have to restart the process all over again. 

This is where I came across the **screen** command , which helps in these kind of situations. 

What is Screen ? 
----------------

Screen command basically allows you to create a session and then detach or attach it. Within the session , you can run any long running process or command. By this way , even if you get disconnected from the host , the process still runs in the host and you can rejoin the session . A session can have multiple windows within , with each window performing some task and you can also switch between the windows.

Useful Screen Commands
----------------------

1. Creating a new Screen Session 

  ```bash
   screen -S <screen name>

   Example : screen -S testscreen

  ```

2. List Current Screens  
   To list the current screens available . 

   ```bash
      
    screen -ls
   ```

3. Attaching to a Screen 
   
   To attach to an existing screen : 

   ```bash
      
    screen -d -R <screen name>

   ```
   The above command first detaches the screen if its attached. It then attaches to the given screen name.

4. Detach a Screen

   If you are within the screen and you want to detach it , you press the Control Key along with A and d.

   ```bash
      
    Press Ctrl+A d
   ```

5. Creating new Windows within a Screen 

   Within an attached screen , you can create multiple windows running multiple commands by pressing Control Key along with A and c.

   ```bash

    Press Ctrl+A c
   ```

6. Switching Among Windows within a Screen

   Inside a screen , you can switch among the windows by pressing Control Key along with A and n.

   ```bash
      
    Press Ctrl+A n
   ```
7. Exiting the Screen 

   To exit from the screen , you simply type exit as you would in a unix terminal.  In case of multiple windows present , the exit closes that specific window. The screen continues to be there until you have exit from all windows. 

   ```bash
      
    exit
   ```
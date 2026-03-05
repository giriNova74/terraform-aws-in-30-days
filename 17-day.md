# AWS Terraform Blue-Green Deployment using Elastic Beanstalk

## Introduction 

Welcome back to Day 17 of our 30 Days of AWS Terraform journey. It is nice to have you here agian ! 
Over the past few days, we've quietly built up little blocks of understanding together. Yesterday, 
we spent time with IAM authentication using Terraform, and even though IAM can feel a bit strict and 
serious, we made it through with patience.

Today, we're opening a new chapter, something practical, something used by real
teams single day, yet something that can feel intimidating when we first hear its 
name: **blue-green deployment**

<img width="492" height="322" alt="image" src="https://github.com/user-attachments/assets/221736cc-9531-4cf3-8938-d93ff6f65036" />

If that phrase feels a bit heavy, that's okay. Most things in tech sound complicated
before someone explains them. And that's exactly what we're going to do today,
breathe through it, and understand it like a story.

It's a concept that might sound big but is actually just a simple idea wrapped in 
slightly fancy name. By the time we reach the end, we'll see how naturally all the 
pieces fit.

Our mini-project today uses AWS Elastic Beanstalk and Terraform to create two separate 
environments i.e. blue and green. We'll package a small application, upload it to S3,
create application versions, and watch how each environment gets its own version of the app.
The most interesting part comes later, where with a simple "swap",traffic can gently
shift from one environment to the other, giving us a sense of how real deployments 
happen with almost no downtime.

So take a breath, settle in, and let's begin our slow and steady walk into the world 
of blue-green deployments together.

## Understading Blue Green Deployment


![MondayMondaysGIF](https://github.com/user-attachments/assets/032bfe75-17c4-46df-89d2-70918df7e974)

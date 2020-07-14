---
nav_title: Amazon Personalize
alias: /partners/amazon_personalize/

description: "This article outlines the partnership between Braze and Amazon Personalize."
page_type: partner

---

# About Amazon Personalize

> Amazon Personalize is like having your very own Amazon.com machine learning recommendation system, 24 hours a day.

Based on over 20 years of recommendation experience, Amazon Personalize enables you to improve customer engagement by powering real-time personalized product and content recommendations, and targeted marketing promotions. Using machine learning, Amazon Personalize creates higher-quality recommendations for your websites and applications. You can get started without any prior machine learning experience using simple APIs to easily build sophisticated personalization capabilities in just a few clicks. Amazon Personalize will process and examine your data, identify what is meaningful, allow you to pick a machine learning algorithm, and train and optimize a custom model based on your data. 

This document will walk you through the process of configuring Amazon Personalize and integrating it into your Braze environment using Connected Content.  This is presented as an example implementation in an ecommerce site published in the [AWS Samples Retail Demo Store](https://github.com/aws-samples/retail-demo-store/).  You can use this integration pattern to implement Amazon Personalize in your own environment.

# Pre-Requisites

You will need to clone the [Retail Demo Store repo](https://github.com/aws-samples/retail-demo-store/) and follow the steps outlined below to deploy the workshop environment to your AWS account.  An AWS account is required to complete the workshop and to run the integration code.

# Integration Architecture

Before you set up Braze to send personalized messages to users, let's review the relevant components required for a typical ecommerce website, using the Retail Demo Store architecture as an example.

[Braze Personalization Architecture]: {% image_buster /assets/img/amazon_personalize/braze-personalize-arch.png}

Braze will send emails to your users based on their behavior or based on attributes of their user profiles.  This data can be used to identify users and to build user profiles that can be used to determine when to message or email users.  

This event data flow will happen in parallel to the same behavioral event data being sent to Amazon Personalize. In this workshop, the demo store uses Amplify to send events to Personalize as shown in the diagram. This data is used to train a recommendations model that can in turn be used by Braze Connected Content to personalize content to users of your mobile and web applications when your Braze campaign runs.  

Braze Connected content will be able to get these recommendations via a recommendation service running in AWS.  Earlier in this workshop, this service was deployed using by the Cloud Formation templates you used to deploy the workshop environment in ECS.
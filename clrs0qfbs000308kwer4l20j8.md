---
title: "Day 78: Creating a Billing Dashboard with Grafana Cloud and AWS CloudWatch"
datePublished: Wed Jan 24 2024 16:47:34 GMT+0000 (Coordinated Universal Time)
cuid: clrs0qfbs000308kwer4l20j8
slug: day-78-creating-a-billing-dashboard-with-grafana-cloud-and-aws-cloudwatch
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706115367110/02c10d46-d5ac-4f3d-a6be-1b7e39fa747d.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

## Introduction

Grafana Cloud provides a robust platform for monitoring and visualization, while AWS CloudWatch offers a wealth of metrics for various AWS services. In this tutorial, we'll guide you through setting up a Grafana dashboard that visualizes AWS billing data using the Grafana Cloud and AWS CloudWatch.

### Prerequisites

* An AWS account with access to billing information.
    
* An EC2 instance running a Linux operating system.
    
* Docker installed on the EC2 instance.
    
* A Grafana Cloud account (create one at https://grafana.com/get).
    

## Step 1: Create Grafana Cloud Account

1. Go to https://grafana.com/get and create a Grafana Cloud account.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706114440055/7db38813-cfa6-47ca-95f0-a0260fa531e2.png align="center")

## Step 2: Set Up Linux Server Dashboard

1. Click on "Create a Dashboard" and choose "Linux Server" dashboard.
    
2. Install the Grafana Agent on your EC2 instance. Generate an API token in Grafana Cloud and run the provided command on your EC2 instance.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706114512931/d839a11d-2f93-4521-9372-02aab7499e0b.png align="center")

1. Update the Grafana Agent config file on your EC2 instance (go to /etc) with the provided code.
    
2. Restart the Grafana Agent.
    

```bash
sudo systemctl restart grafana-agent
```

1. Test the connection.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706114600440/846eddeb-17e5-48e3-bd3c-f297f6d28bc7.png align="center")

## Step 4: View Linux Node Metrics

1. In the "Explore" section, select 'Linux Node/CPU and System.'
    
2. Observe CPU data. Run a Docker container on your EC2 instance to increase CPU usage and witness real-time updates.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706114631146/9f2065f4-c278-4604-bead-04394b8af8d5.png align="center")

## Step 5: Connect AWS CloudWatch

1. In Grafana Cloud, go to "Settings" and choose "Data Sources."
    
2. Click on "Add your first data source" and choose "CloudWatch."
    
3. Provide the AWS IAM user's username and password with programmatic access.
    
4. Select the region as 'us-east-1.'
    
5. Click on "Save & Test" to verify the connection.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706114674907/58548c0a-f743-438c-baeb-21233603abf2.png align="center")

## Step 6: Create Billing Dashboard

1. Navigate to the "Dashboards" section.
    
2. Look for a dashboard named 'Billing/Usage'.
    
3. Click on the dashboard to view the preconfigured panels displaying billing and usage metrics.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706114691109/e4eb20d1-d07d-4d96-a8d6-60d09c92e6ea.png align="center")

## Conclusion

Congratulations! You've successfully set up a Grafana dashboard that integrates with AWS CloudWatch to visualize billing data. This powerful combination allows you to monitor your AWS spending efficiently. Feel free to explore more visualizations and metrics to enhance your monitoring capabilities. Happy monitoring!

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.
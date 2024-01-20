---
title: "Day 74: Connecting EC2 with Grafana"
datePublished: Sat Jan 20 2024 13:09:13 GMT+0000 (Coordinated Universal Time)
cuid: clrm3678r000a0al8h2ko6q5n
slug: day-74-connecting-ec2-with-grafana
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705756091937/04fe4cc2-2e50-4854-8191-5b81215aec8f.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

## Introduction

Monitoring the performance of your server infrastructure is crucial for ensuring optimal operation and identifying potential issues. In this tutorial, we'll explore how to set up Grafana and Prometheus to monitor CPU usage on Ubuntu instances. Grafana provides a powerful visualization interface, while Prometheus collects and stores metrics.

## Prerequisites

Before we begin, make sure you have:

* Two Ubuntu instances running on your preferred cloud provider (e.g., AWS, Azure).
    
* SSH access to both instances.
    
* Basic knowledge of Ubuntu commands and Prometheus/Grafana.
    

## Step 1: Install Grafana on Ubuntu

```
sudo apt-get update
sudo apt-get install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install -y grafana
sudo systemctl enable grafana-server
sudo systemctl start grafana-server
```

Access Grafana by navigating to `http://<your-ubuntu-instance-ip>:3000` in your browser, using the default login credentials (admin/admin).

## Step 2: Configure Prometheus Data Source in Grafana

1. Log in to Grafana.
    
2. Go to "Settings" &gt; "Data Sources."
    
3. Click "Add your first data source."
    
4. Choose "Prometheus" and enter the IP address of the second Ubuntu instance where Prometheus will run.
    

## Step 3: Install Prometheus on the Second Ubuntu Instance

SSH into the second Ubuntu instance:

```
sudo apt-get update
sudo apt-get install -y prometheus
sudo systemctl enable prometheus
sudo systemctl start prometheus
```

## Step 4: Configure Prometheus as a Data Source in Grafana

1. Log in to Grafana.
    
2. Go to "Settings" &gt; "Data Sources."
    
3. Click "Add your first data source."
    
4. Choose "Prometheus" and enter the IP address of the second Ubuntu instance.
    

## Step 5: Create CPU Usage Dashboard in Grafana

1. In Grafana, go to the "+" menu on the left sidebar and choose "Dashboard."
    
2. Add a new panel.
    
3. Select the Prometheus data source.
    
4. Use the following query to monitor user CPU usage:
    
5. ```bash
    rate(node_cpu_seconds_total{mode="user"}[1m])
    ```
    
6. Configure visualization settings and save the panel.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705756002620/0bef3143-590c-4e81-8b9d-9a3f116fbccc.png align="center")

## Step 6: Explore and Analyze Metrics

Explore the Grafana dashboard to visualize and analyze CPU usage metrics from both Ubuntu instances. Customize panels and queries based on your monitoring requirements.

## Conclusion

Setting up Grafana and Prometheus on Ubuntu allows you to efficiently monitor CPU usage and other system metrics. This tutorial provides a basic configuration, and you can expand on it to include additional metrics and visualizations according to your specific needs.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.
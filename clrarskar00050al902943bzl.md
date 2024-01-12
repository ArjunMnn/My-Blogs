---
title: "Day 72 & 73: Grafana"
datePublished: Fri Jan 12 2024 15:05:13 GMT+0000 (Coordinated Universal Time)
cuid: clrarskar00050al902943bzl
slug: day-72-73-grafana
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705071827886/ce7a3714-bcaf-4b75-bdc1-bd69997adc09.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

In the realm of monitoring and observability, Grafana has emerged as a powerful and versatile tool, empowering users to gain insights through intuitive visualizations. In this blog post, we'll delve into what Grafana is, its key features, why it's preferred, the types of monitoring it facilitates, compatible databases, and the nuances between Grafana and Prometheus. Additionally, we'll provide step-by-step instructions on setting up Grafana on a Linux system.

## What is Grafana?

Grafana is an open-source analytics and monitoring platform designed to visualize and analyze metrics from various data sources. It provides a centralized platform for creating, exploring, and sharing dashboards, enabling users to gain a holistic view of their system's performance and health.

## Key Features of Grafana:

### 1\. Extensive Data Source Support:

Grafana supports a wide range of data sources, including popular databases like Prometheus, InfluxDB, Elasticsearch, and more. This flexibility allows users to consolidate and visualize metrics from various systems within a unified dashboard.

### 2\. Intuitive Dashboards:

With a user-friendly interface, Grafana facilitates the creation of customizable dashboards. Users can choose from a variety of panels and charts to represent data in a way that suits their specific monitoring needs.

### 3\. Alerting and Notifications:

Grafana provides robust alerting capabilities, allowing users to set up alerts based on specific conditions. Notifications can be sent via various channels, ensuring that critical issues are promptly addressed.

### 4\. Community and Plugin Support:

A vibrant community and a vast repository of plugins contribute to Grafana's extensibility. Users can enhance functionality by integrating plugins for additional data sources, visualizations, and alerting mechanisms.

## Why Choose Grafana?

The appeal of Grafana lies in its versatility and adaptability. It caters to a broad spectrum of use cases, from infrastructure monitoring to business intelligence. Its open-source nature, coupled with an active community, ensures continuous improvement and the availability of valuable resources.

## Monitoring with Grafana:

Grafana facilitates various monitoring types, including:

### 1\. Infrastructure Monitoring:

Track the health and performance of servers, networks, and other infrastructure components.

### 2\. Application Monitoring:

Monitor application metrics, logs, and traces to identify bottlenecks and optimize performance.

### 3\. Business Metrics:

Visualize business-related metrics, helping organizations make data-driven decisions.

## Databases Compatible with Grafana:

Grafana seamlessly integrates with databases like:

* Prometheus
    
* InfluxDB
    
* Graphite
    
* Elasticsearch
    
* MySQL
    
* PostgreSQL, and more.
    

## Metrics and Visualizations:

Metrics represent quantifiable data points, while visualizations in Grafana transform these metrics into meaningful charts and graphs. Grafana supports a variety of visual elements, including line graphs, bar charts, heatmaps, and more, providing a comprehensive view of data trends.

## Grafana vs. Prometheus:

While Grafana and Prometheus often work together, they serve distinct purposes. Prometheus is primarily a monitoring and alerting toolkit, while Grafana is an analytics and visualization platform. Prometheus collects and stores metrics, and Grafana pulls these metrics to create insightful dashboards.

## Setting Up Grafana:

Now, let's walk through the steps to set up Grafana on a Linux system:

1. Install prerequisite packages:
    

```bash
sudo apt-get install -y apt-transport-https software-properties-common wget
```

1. Import the GPG key:
    

```bash
sudo mkdir -p /etc/apt/keyrings/
wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
```

1. Add a repository for stable releases:
    

```bash
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

1. Update the list of available packages:
    

```bash
sudo apt-get update
```

1. Install Grafana OSS:
    

```bash
sudo apt-get install grafana
```

1. Enable and start Grafana service:
    

```bash
sudo systemctl enable grafana-server
sudo systemctl start grafana-server
```

1. Check the status:
    

```bash
sudo systemctl status grafana-server
```

Now launch Grafana by going to `<ipaddress>:3000` in your browser. Make sure port 3000 is open in the ec2 instance security group.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705071819433/781c9a90-ec3c-48e4-ad8b-96c3ca2dba07.png align="center")

## Conclusion

Grafana is a powerful, adaptable monitoring solution with a user-friendly interface and broad data source support. Its seamless integration with popular databases simplifies infrastructure and application monitoring. The straightforward installation guide enables users to quickly harness Grafana's capabilities for creating insightful dashboards.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.
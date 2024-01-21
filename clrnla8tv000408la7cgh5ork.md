---
title: "Day 75 & 76: Monitoring Docker Logs Using Grafana and Prometheus"
datePublished: Sun Jan 21 2024 14:24:01 GMT+0000 (Coordinated Universal Time)
cuid: clrnla8tv000408la7cgh5ork
slug: day-75-monitoring-docker-logs-using-grafana-and-prometheus
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705846886389/f1d5d91e-da30-4f4b-bfa9-afdb511cabc8.png
tags: cloud, docker, aws, devops, 90daysofdevops

---

## Introduction

In this comprehensive tutorial, we'll guide you through the process of sending Docker logs to Grafana for effective monitoring and visualization. This setup involves launching two EC2 instances, installing Grafana on Instance 1, and Prometheus with Docker on Instance 2. By the end of this guide, you'll have a fully functional Grafana dashboard displaying Docker container metrics.

### Prerequisites

* AWS account with EC2 instances
    
* Basic knowledge of Linux commands
    
* SSH access to both EC2 instances
    

## Step 1: Launch EC2 Instances

Launch two EC2 instances on AWS, naming them Instance 1 and Instance 2. Ensure you have the necessary security groups, key pairs, and IAM roles configured for smooth communication.

## Step 2: Install Grafana on Instance 1

SSH into Instance 1 and install Grafana using the following commands:

```bash
sudo apt-get update
sudo apt-get install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install -y grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

Access Grafana's web interface by navigating to `http://<instance_1_ip>:3000` in your browser. Default login credentials are usually admin/admin.

## Step 3: Install Prometheus and Docker on Instance 2

SSH into Instance 2 and install Prometheus and Docker:

```bash
sudo apt-get update
sudo apt-get install -y prometheus docker.io
```

## Step 4: Configure Docker Metrics Collection

Create a file named `daemon.json` in `/etc/docker/` with the following content:

```bash
{
    "metrics-addr": "0.0.0.0:9323",
    "experimental": true
}
```

Restart Docker:

```bash
sudo systemctl restart docker
```

You should now see your docker metrics by going to `<instance_2_ip>:9323/metric.`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705847008057/4fa954f7-e29c-4aea-a240-1fd110e3033e.png align="center")

## Step 5: Configure Prometheus for Docker Metrics

Edit the `prometheus.yml` file in `/etc/prometheus/` and add a new job:

```bash
- job_name: 'docker_metrics'
  static_configs:
    - targets: ['<instance_2_ip>:9323']
```

Restart Prometheus:

```bash
sudo systemctl restart prometheus
```

Verify the new job is visible in Prometheus targets.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705846781631/e95c15e6-0975-49a8-b4ae-42046501f30f.png align="center")

## Step 6: Configure Grafana Data Source

1. Log in to Grafana.
    
2. Navigate to "Settings" &gt; "Data Sources."
    
3. Click "Add your first data source" and select Prometheus.
    
4. Set the URL to `<instance_2_ip>:9090` and click "Save & Test."
    

## Step 7: Create Grafana Dashboard

1. Go to the "+" icon on the left sidebar and select "Dashboard."
    
2. Click "Add new panel" and choose Prometheus as the data source.
    
3. Use the sample query:
    
    ```bash
    engine_daemon_container_states_containers{state="running"}
    ```
    
4. Customize the panel and dashboard as needed.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705846670317/fa60ebb2-4f2b-4a3a-a409-82bf0b517e26.png align="center")

## Conclusion

Congratulations! You've successfully set up Grafana to visualize Docker container metrics collected by Prometheus. This comprehensive guide ensures you have a smooth experience from launching EC2 instances to creating a functional Grafana dashboard. Feel free to explore more queries and customize your dashboard for a tailored monitoring solution.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.
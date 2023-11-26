---
title: "Day 31: Launching your First Kubernetes Cluster with Nginx running"
datePublished: Sun Nov 26 2023 07:01:59 GMT+0000 (Coordinated Universal Time)
cuid: clpf4u3pa000b09jp7x69fohd
slug: day-31-launching-your-first-kubernetes-cluster-with-nginx-running
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700982068204/8cf6c28e-2073-47b3-ab8a-d0a0fbf86bd9.png
tags: software-development, kubernetes, devops, software-engineering

---

# **💥Introduction**

Embark on a hands-on Kubernetes journey with our latest blog post!

After grasping the core architecture of the pivotal tool - Kubernetes, it's time to dive into action.

Enter Minikube, your gateway to swiftly set up a local Kubernetes cluster on macOS, Linux, or Windows.

Minikube simplifies the Kubernetes experience, enabling deployment as a VM container, or **bare metal**.

Our blog guides you through installing Minikube and understanding Pods - the fundamental units of Kubernetes computing.

Unleash the power of Kubernetes in a user-friendly, local environment - the adventure begins here.

# **📚Understanding Minikube: A Closer Look**

Minikube emerges as a lightweight and open-source solution that empowers developers to establish a singular-node Kubernetes cluster right on their local machines. This ingenious tool is tailored for streamlining local application testing and development within the Kubernetes framework, eliminating the need for complex cluster setups.

# **📖Features of Minikube**

**1\. Local Kubernetes Cluster:** Minikube stands as a conduit for creating a solo-node Kubernetes cluster on personal computers, cultivating an environment perfect for the evaluation and advancement of applications.

**2\. Cross-platform Compatibility:** One of Minikube's strengths is its adaptability across diverse operating systems like Windows, macOS, and Linux, making it accessible to a wide developer audience.

**3\. Efficient Cluster Management:** Developers enjoy the convenience of seamlessly initiating, pausing, and deleting clusters, facilitating rapid iterations during the development phase.

**4\. Expandable with Add-ons and Plugins:** Minikube extends its prowess through various add-ons and plugins, enabling users to personalize the cluster's behavior and incorporate supplementary functionalities as necessary.

**5\. Simplified Deployment:** The deployment of Kubernetes workloads becomes an uncomplicated process, rendering Minikube an optimal choice for localized development, experimentation, and learning.

**6\. Seamlessly Integrated with Docker:** Minikube effortlessly integrates with Docker, empowering developers to employ their existing Docker images within the Kubernetes landscape.

**7\. Adapting to Resource Constraints:** Users wield the ability to define resource limits for the virtual machine hosting the Kubernetes cluster, rendering Minikube suitable for systems with constrained resources.

**8\. Managing Kubernetes Versions:** Minikube grants developers the liberty to select precise versions of Kubernetes for operation, ensuring alignment with the target environment of their applications.

# **🚀Exploring the Concept of Pods**

**Defining a Pod:** In Kubernetes, a Pod stands as the smallest executable entity, embodying a single instance of a functioning process.

This versatile unit may comprise one or multiple closely linked containers that share a common network space, facilitating internal communication through the local host.

Scheduled onto nodes within the cluster, Pods can be scaled both upwards and downwards. They cultivate an isolated environment for applications, encompassing shared resources such as storage volumes and IP addresses.

Pods are conceived to be transitory, effortlessly replaceable or rescheduled in the event of disruptions.

# **📃Task: Setting Up Minikube on Local**

Follow these step-by-step instructions to create an optimal environment, install Docker, Minikube, and Kubelet, and ensure the Minikube cluster is operational:

**Step 1: Set Up a New VM Instance**

1. Within your preferred virtualization platform (here EC2 instance with t2.medium), generate a new VM instance using the following specifications:
    
    * CPU: 2
        
    * Memory: 4GB
        
    * Disk Space: 20GB
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692790118523/a4bd0bfc-0350-4565-b1b9-2b39461249a4.png?auto=compress,format&format=webp align="left")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692790317453/98a567f0-eb69-491c-a14d-24325820678a.png?auto=compress,format&format=webp align="left")
        

**Step 2: Installing Docker**

1. Access your VM instance through SSH.
    
2. Update the package repository:
    

```dockerfile
 sudo apt update
```

Install the necessary essential packages with the following command, This command will install the packages `curl`, `wget`, and `apt-transport-https` on your system.

```dockerfile
sudo apt install -y curl wget apt-transport-https
```

* Install Docker:
    

```dockerfile
 sudo apt install docker.io
```

```dockerfile
 sudo usermod -aG docker $USER
```

* Start Docker and enable it to launch on system startup:
    

1. ```dockerfile
      sudo systemctl start docker
      sudo systemctl enable docker
    ```
    

**Step 3: Minikube Integration**

1. Download the Minikube binary using `curl` Make it executable and move it into your path:
    

* ```dockerfile
       curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
       chmod +x minikube
       sudo mv minikube /usr/local/bin/
    ```
    
* Confirm the presence of Minikube:
    

1. ```dockerfile
      minikube version
    ```
    

**Step 4: Kubectl Install**

1. Download kubectl, which is a Kubernetes command-line tool.
    

* ```dockerfile
       curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    ```
    
* Make it executable and move it into your path
    

1. ```dockerfile
      chmod +x kubectl
      sudo mv kubectl /usr/local/bin/
    ```
    

**Step 5: Activating Minikube and Checking Status**

1. Start Minikube :
    

* ```dockerfile
       minikube start --driver=docker
    ```
    
* Review Minikube's operational status:
    

1. ```dockerfile
      minikube status
    ```
    

**Step 6: Verifying the Minikube Cluster**

1. Confirm the operational status of the Minikube cluster:
    

* ```dockerfile
       kubectl get nodes
    ```
    
    This should indicate the Minikube node as "Ready."
    
* Inspect the statuses of pods and namespaces:
    

1. ```dockerfile
      kubectl get pods --all-namespaces
    ```
    
    This action will display active pods categorized within various namespaces within the Minikube cluster.
    

**Step 7: Stop & Delete(Optional**) **the Minikube Cluster**

```dockerfile
#When you are done, you can stop the Minikube cluster with:
minikube stop

#If you wish to delete the Minikube cluster entirely, you can do so with:
minikube delete
```

**That's it! You've successfully installed Minikube on Ubuntu, and you can now start deploying Kubernetes applications for development and testing.**

# **Running Nginx using minikube**

Step 1: Start Minikube Cluster

```dockerfile
minikube start
```

Step 2: Deploy Nginx Container

```dockerfile
kubectl run nginx-deployment --image=nginx --port=80
```

This command creates a deployment named `nginx-deployment` with one replica, using the Nginx Docker image and exposing port 80.

Step 3: Expose the Nginx Deployment

```dockerfile
kubectl expose deployment nginx-deployment --type=NodePort
```

This command creates a NodePort service to expose the Nginx deployment.

Step 4: Get Service URL

```dockerfile
minikube service nginx-deployment --url
```

This command retrieves the URL to access the Nginx service. Open the provided URL in your web browser to view the Nginx welcome page.

# **🌈Conclusion**

In summary, the Minikube setup process equips you to explore Kubernetes effortlessly.

With Docker, `kubectl`, and essential packages in place, you've established a local cluster, laying the foundation for container orchestration understanding.

Minikube provides a safe playground to experiment, enabling hands-on exploration of Kubernetes intricacies and application deployment.

This journey empowers you to confidently navigate container orchestration, setting the stage for further Kubernetes mastery.
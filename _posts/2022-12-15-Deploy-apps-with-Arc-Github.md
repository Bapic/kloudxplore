---
layout: post
title:  "Deploy apps to Azure-Arc enabled Kubernetes cluster using 'Cluster Connect' and 'GitHub Actions'"
date:   2023-02-15 11:38:18 +0000
categories: Azure hybrid and multicloud
---
**---Work in progress---**

# Deploy apps to Azure-Arc enabled Kubernetes cluster using 'Cluster Connect' and 'GitHub Actions'

Azure-Arc enabled Kubernetes helps you to organize, inventory, manage, monitor and secure Kubernetes clusters hosted outside of Azure from a single control pane. The cluster could reside anywhere on-premises, any cloud service provider (AWS, GCP, Azure, Alibaba etc.) or in any edge location in your enterprise. Read more about Azure-Arc enabled Kubernetes here.  

## Scenario

Suppose you are the Infrastructure admin of a large enterprise that consists of multiple Kubernetes workload across multiple cloud providers and on-premises. Your organization adopted Azure Arc for unified operations for management, monitoring, security. You have several Kubernetes clusters behind a firewall, protected in a specific virtual network perimeter and only specific incoming and outgoing traffic are allowed depending on workload requirements. In such scenarios, your Kubernetes API server endpoint, DNS FQDN resolution will have restricted access. Your nodes and API server communication remain on the private network only. Only required application and service traffic are allowed. One of the challenges of such environment is that it does not support cloud hosted CI/CD agents such as Azure DevOps Microsoft-hosted agents or GitHub hosted runners. You will need an agent VM which can access the cluster from within the network perimeter such as self-hosted Azure DevOps agents or self-hosted runners. For those who require more control and security, this is the way to go. However, in certain cases with Dev/Test environment or wherein you would like to focus on productivity and less maintenance overhead, you would like to use the cloud-hosted agents for build and deploy.

![Alt text](/kloudxplore/images/githubaction-k8sarc-soln.png)
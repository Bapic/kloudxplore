---
layout: post
title:  "Deploy apps to Azure-Arc enabled Kubernetes cluster using 'Cluster Connect' and 'GitHub Actions'"
date:   2023-02-15 11:38:18 +0000
categories: Azure hybrid and multicloud
---

Azure-Arc enabled Kubernetes helps you to organize, inventory, manage, monitor and secure Kubernetes clusters hosted outside of Azure from a single control pane. The cluster could reside anywhere on-premises, any cloud service provider (AWS, GCP, Azure, Alibaba etc.) or in any edge location in your enterprise. Read more about [Azure-Arc enabled Kubernetes][arc-enabled-kubernetes].  

## Scenario

Suppose you are the Infrastructure admin of a large enterprise that consists of multiple Kubernetes workload across multiple cloud providers and on-premises. Your organization adopted Azure Arc for unified operations for management, monitoring, security. You have several Kubernetes clusters behind a firewall, protected in a specific virtual network perimeter and only specific incoming and outgoing traffic are allowed depending on workload requirements. In such scenarios, your Kubernetes API server endpoint, DNS FQDN resolution will have restricted access. Your nodes and API server communication remain on the private network only. Only required application and service traffic are allowed. One of the challenges of such environment is that it does not support cloud hosted CI/CD agents such as Azure DevOps Microsoft-hosted agents or GitHub hosted runners. You will need an agent VM which can access the cluster from within the network perimeter such as self-hosted [Azure DevOps Agents][azure-devops-agents] or [self-hosted runners][self-hosted-runners]. For those who require more control and security, this is the way to go. However, in certain cases with Dev/Test environment or wherein you would like to focus on productivity and less maintenance overhead, you would like to use the cloud-hosted agents for build and deploy.

## Solution

In this exercise we will learn how to use **Cluster Connect** and **GitHub Actions** to build and deploy a sample application to a Arc-enabled Kubernetes cluster. Here is a diagram to illustrate the solution and steps to achieve the same.

*Disclaimer*: *The steps mentioned below are for non-production, test or experimental learning scenarios only. It will help you to understand and take an informed decision on its usage. Once confident, you can create a more robust production ready solution.*

![Alt text](/kloudxplore/images/githubaction-k8sarc-soln.png)

## Implementation steps

The implementation steps includes several hands-on activities which are elaborated here in my [Microsoft Tech Community article][tech-community] and also in my [github doc file][github-doc-file].

## Conclusion

I hope you enjoyed the steps-by-step guide above and was able to experience this cool implementation using Cluster Connect and GitHub Actions. For production environments additional security and configurations etc. will be required. There is one more alternative that you can use in such closed environments - GitOps. All these and much more we will explore in upcoming post. Hope you found this post useful. Stay tuned for more.

[arc-enabled-kubernetes]: https://learn.microsoft.com/en-us/azure/azure-arc/kubernetes/overview
[self-hosted-runners]: https://docs.github.com/en/enterprise-server@3.2/actions/hosting-your-own-runners/about-self-hosted-runners
[azure-devops-agents]: https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/agents?tabs=browser&view=azure-devops 
[github-doc-file]: https://github.com/Bapic/gh-arc-app-deploy 
[tech-community]: https://techcommunity.microsoft.com/t5/azure-arc-blog/deploy-apps-to-azure-arc-enabled-kubernetes-cluster-using/ba-p/3286541
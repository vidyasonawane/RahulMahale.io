+++ 
date = "2017-11-07"
title = "Talk at DevOpsDays Capetown(South Africa) on “Deploying production ready kubernetes clusters: Lessons learnt”"
slug = "" 
tags = []
categories = ["Talks"]

+++

Kubernetes has proved itself as a Production grade container orchestration tool as almost 71% of companies in the container world use it as a container orchestration tool. 

Planning to use Kubernetes in production for cloud-native apps? Concerned about how to integrate a Kubernetes cluster into your existing infrastructure!! This talk will brief you through some of the common challenges when deploying Kubernetes cluster on Public cloud like AWS and how to address those challenges.

We will show on how to provision and deploy production ready kubernetes cluster using tools like Kops. Some of the points I will try to cover:-

**Highly available kubernetes cluster, deploying multi master cluster in different data center regions.**

* Auto-scaling up and down kubernetes cluster.
* Private networking (Calico/Weave/Flannel etc).
* Monitoring kubernetes cluster using Prometheus and Grafana
* Backup and restore Kubernetes Cluster.
* Resource management.
* Security policies.
* User management.


**Application deployment considerations on kubernetes clusters considerations.**

* Zero down time deployments.
* Auto-scaling applications using Horizontal Pod auto-scaler and Memory based auto-scaler.
* Deploying apps in different Name-spaces.
* Effectively using Persistent volume and stateful sets.
* When to use jobs and scheduled jobs.
* Logging and Monitoring of applications.


At the end of the talk, attendees will be able to understand how to deploy kubernetes production ready cluster. And best practices to deploy apps on Kubernetes. video of the talk is [here](https://www.youtube.com/watch?v=xlYvWwdjXNE)
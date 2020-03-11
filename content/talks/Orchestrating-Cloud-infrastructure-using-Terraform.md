+++ 
date = "2016-03-19"
title = "Talk at FOSSASIA Singapore on “Orchestrating Cloud infrastructure using Terraform”"
slug = "" 
tags = []
categories = ["talks"]

+++

Terraform is an open-source tool for building, changing, and versioning infrastructure safely and efficiently. 
Terraform can manage existing and popular service providers as well as custom in-house solutions. We can use it to build the infrastructure in many cloud providers such as AWS, Azure, Rackspace, DigitalOcean, GoogleCloud, Docker, OpenStack etc. Moreover it has an provisioners like chef, which we can use to automate for configuration Management. It can be seen as similar to cloud-formation from AWS. 

Within this short workshop with this tool I am creating a basic two-tier infrastructure stack in a single command. What I will do it in one stroke of command is Create a complete infrastructure in AWS VPC running an app server, What are the things happening in this one command:
 - Creating a VPC.
 - Creating a subnets one public and private.
 - Creating respective security groups and rules. 
 - Creating a load balancer. 
 - Creating a app server running an web server called nginx. 
 - Attaching a server to ELB and giving us a public DNS by which we can access the app. 
 - And it gives a simple sketch diagram of our infrastructure as well. 
 
 Thus we have full fledged app running on Cloud in single Command. 
 
 Links : 
 
 https://www.terraform.io

 https://github.com/hashicorp/terraform

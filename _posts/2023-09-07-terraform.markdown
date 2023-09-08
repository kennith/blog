---
title: Terraform
layout: post
categories: ["thoughts", "terraform"]
---
Terraform is a great tool to manage the cloud resources. 

When I first started managing the AWS infrastructure, I started with the "click" ops. It means, I am clicking on VPC, EC2, RDS on the AWS web console. 

It is not the most efficient way to manage the cloud resources if I need to duplicate it in different regions. The worst of all, "click ops" is error prone. 

AWS offers CloudFormation, though it solved my problem, but I did not enjoy writing the cloud infrastructure with CloudFormation at all. 

I attend the AWS reInvent conference, I stumbled into the AWS CDK talk. I told myself, this is it. A language I am familiar with (as a software engineer working closely with PHP and JavaScript) and the experience writing infrastructure as code was a big improvement. It solved my problem, but it felt writing CDK is like writing an app to provision cloud resources. 

Then, on the next AWS reInvent conference, I stumbled into Terraform. I think it was 2019 and Mitchell was in the panel and I do not know anything about it except the content is infrastructure as code something. Anyway, after the talk, I say to myself, this is it! I am familiar with Packer, an excellent tool when I used it for Laravel Homestead, and later on preparing AWS images. The HCL syntax was easy to read and to learn. It was such an elegant solution. `terraform validate`, `terraform apply`, `terraform plan`. These are just some of the valuable tools available for building cloud infrastructure. 

I am quite happy with Terraform for delivering such enjoyable developer experience. 
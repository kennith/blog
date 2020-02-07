---
title: EC2 Image Builder
layout: post
---
<img src="https://dv4pe9668mr4p.cloudfront.net/1580933164235/assets/img/How-it-works.png">

The EC2 Image Builder creates a "Golden Image" for running EC2 instances. It is the most basic form of using AWS EC2 before Docker or Kubernetes were introduced. 

The problem it solved for me is I can build my AMI directly on AWS platform instead of calling the API from my CI/CD provider, e.g. CircleCI or GitLab.

I can quickly learn how to create components by using the AWS defined template as a starter template. The tests gives me confidence of the build. I like it. 

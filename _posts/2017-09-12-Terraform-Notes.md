---
layout: post
title: Terraform Notes
tags: 
category: Tech
---

- init
- import
- apply
- plan
- destroy

# Getting terraform states  

terraform init  # creates a .terraform folder with empty states
terraform import module.ps-ledger-dist-sit-blue.aws_cloudfront_distribution.monkey XXXXXXXXXXXXXX    # module folder > ps ledger name > 

Check out main.tf to figure out path

It doesn't matter how many files are in the folder, these files are collapsed into one file  

# How to get the state back

terraform import 

backend.tf - tells terraform that the state is held remotely

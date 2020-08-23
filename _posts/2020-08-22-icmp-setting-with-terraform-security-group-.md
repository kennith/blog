---
title: ICMP Setting with Terraform Security Group 
layout: post
categories: ['terraform', 'aws']
---
The ICMP setting on [AWS security group](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group).

```hcl
ingress {
    protocol    = "icmp"
    cidr_blocks = ["0.0.0.0/0"]
    from_port   = 8 # ICMP type number
    to_port     = 0 # ICMP code
}
```

If the protocol is `ICMP`, the `from_port` is the ICMP type number and `to_port` is ICMP code. 

Reference using [ICMP Control Message](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol#Control_messages), the echo request, e.g. `ping` command, to allow a machine to take a request from outside, type `8` must be opened. When protocol is ICMP, `from_port` becomes `ICMP type number` and `to_port` becomes `ICMP code`. Since  `echo request` in ICMP type is `8`, `echo request` in ICMP code is `0`, therefore, the `from_port` in this case is `8` and the `to_port` is `0`. 

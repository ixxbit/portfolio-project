# VPN Architecture Components

![](../../../.gitbook/assets/image%20%2841%29.png)

## VPC



![](../../../.gitbook/assets/image%20%2823%29.png)



## Route Table

![Route Table ](../../../.gitbook/assets/image%20%2837%29.png)

1. Route table specifies how **system B** can communicate with **system A**.
2. Router routes pockets accordingly.

2. 

## Elastic IP

![](../../../.gitbook/assets/image%20%2851%29.png)

* Is a static public IP address that points to your Elastic Network Interfaces \(ENI card\)

{% hint style="info" %}
Whenever assigning static/dynamic IP address to EC2, you  always asign it to an ENI

* example: you can have two elastic IP addresses and your original server goes down
  *  SOLUTION: you just spin up a new server and move the ENI from original server to the new server and still continue using the same IP addresses withought having to worry about DNS server settings
{% endhint %}

## Internet Gateway

![](../../../.gitbook/assets/image%20%2834%29.png)

A door at your VPC that allows inbound/outbound communication with your VPC components, i.e. a web server






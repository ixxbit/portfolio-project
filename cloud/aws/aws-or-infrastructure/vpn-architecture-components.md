# VPC Architecture Components

source: [https://www.youtube.com/watch?v=LX5lHYGFcnA](https://www.youtube.com/watch?v=LX5lHYGFcnA)

![](../../../.gitbook/assets/image%20%2889%29.png)

## VPC



![](../../../.gitbook/assets/image%20%2850%29.png)

VPC is composed of multiple private and public subnets within Availability Zones throughout an AWS Region.

## Route Table

![Route Table ](../../../.gitbook/assets/image%20%2880%29.png)

1. Route table specifies how **system B** can communicate with **system A**.
2. Router routes pockets accordingly.

2. 

## Elastic IP

![](../../../.gitbook/assets/image%20%28107%29.png)

* Is a static public IP address that points to your Elastic Network Interfaces \(ENI card\)

{% hint style="info" %}
Whenever assigning static/dynamic IP address to EC2, you  always asign it to an ENI

* example: you can have two elastic IP addresses and your original server goes down
  *  SOLUTION: you just spin up a new server and move the ENI from original server to the new server and still continue using the same IP addresses withought having to worry about DNS server settings
{% endhint %}

## Internet Gateway

![](../../../.gitbook/assets/image%20%2871%29.png)

A door at your VPC that allows inbound/outbound communication with your VPC components, i.e. a web server

## NAT Gateway

![](../../../.gitbook/assets/image%20%2879%29.png)

## VPN Connection

![](../../../.gitbook/assets/image%20%2877%29.png)

Three components to create a VPN connection

### Customer Gateway

On my site I need my Customer Gateway \(basically my router on my premises\)

### VPNC Connection

VPN iPSec tunnel connection

### Virtual Private Gateway

The router/gateway on the aws VPC



## NAT Gateway

￼ ￼￼￼

![](../../../.gitbook/assets/image%20%2899%29.png)

 ￼￼ ￼

* Nat gateway sits in a public subnet:
  * A DB server in private subnet needs to update...
    * the DB talks to NAT Gateway
    * then it forwards the communication out to the Internet Gateway and can talk to outside world
    * The NAT remembers what port the request was sent out AND that it was sent from the database in the private subment
      * IT will NOT allow any new communication or connections in the database.

## VPC Peering

![](../../../.gitbook/assets/image%20%28109%29.png)

Send a request from one VPC to another and accept request to get connected.

## VPC Endpoints

![](../../../.gitbook/assets/image%20%2829%29.png)

Connectivity that allows you to connect to certain AWS services privately i.e. EC2 with S3


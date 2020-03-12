---
description: Setup and Configure Your AWS VPC
---

# Getting Started With AWS VPC

## 1. Create VP

![](../../../.gitbook/assets/image%20%28105%29.png)

{% hint style="warning" %}
By default, when you create a VPC, it doesn't do DNS hostnames resolutions

* Select your VPC &gt; Actions &gt; Edit DNS Hostnames &gt; Yes
* This way I can launch instances with DNS hostnames 
{% endhint %}

## 2. Create Subnets

* Two Availability Zones
  * One public subnet
  * One private subnet

![](../../../.gitbook/assets/image%20%286%29.png)

## 3. Create Internet Gateway and Route Tables

### a. Create Internet Gateway

### b. Attach IGW to my VPC

* by default VPC have a MAIN \(default\) route table.  New subnets automatically get assigned the main default table
* A subnet MUST be associated with a particular Route Table.  Otherwise  

### c. Create Route Tables

* Public Route Table and Private Route Tables
* Associate each table with the subnets accordingly

### d. Route Propagation

* by default it propagates to every router in the network

_by default, when creating route tables they have local access within vpn_

\_\_

## _4. Create EC2_

![](../../../.gitbook/assets/image%20%2871%29.png)

![](../../../.gitbook/assets/image%20%2814%29.png)

![](../../../.gitbook/assets/image%20%2890%29.png)

### _Create Security Groups_

![](../../../.gitbook/assets/image%20%2889%29.png)

![](../../../.gitbook/assets/image%20%2845%29.png)

![](../../../.gitbook/assets/image%20%28122%29.png)

![](../../../.gitbook/assets/image%20%285%29.png)

## Create Internet Gateway




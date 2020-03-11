# VPC Setup and Configuration

{% hint style="info" %}
Related tasks: [AWS \| labs](../aws-or-labs/labs.md)
{% endhint %}

## 

## KEY POINTS

![](../../../.gitbook/assets/image%20%2887%29.png)

## I. SPECIFY VPN NETWORK/SUBNET

![](../../../.gitbook/assets/image%20%2857%29.png)

* My VPC main network subnet is larger enough /16
* Make noticeable subnet ranges between timezones 

## II. CONFIGURE ROUTE TABLE RULES

{% hint style="info" %}
* The routing table decides wether a subnet in my VPC is a public subnet or private subnet.
* By default everything within a VPC are able to communicate with each other regardless of what additional rules their associated table specifies. Their is always a local route specified
{% endhint %}

### Scenario 1: Local communication

![](../../../.gitbook/assets/image%20%28110%29.png)

* it's obvios that 10.0.3.48 is part of the the local network \(source\) so it gets routed from subnet a to subnet b.

### Scenario 2: Public communication

![](../../../.gitbook/assets/image%20%2835%29.png)

* 53.19.1.4 is not part of the local subnet 10.0.0.0/16 -- RESULT: No MATCH
* The other rule entry says that any IP address \(from 0.0.0.0/0\) will be sent to IGW

### Scenario 3: Public  and Private Route Tables

![](../../../.gitbook/assets/image%20%2839%29.png)

#### Public Route Table

* has two rule entires one from local components within the vpc 
* the other from any component to the internet gateway

#### Private Route Table

* has only one entry for internal components to communicate locally only 

![](../../../.gitbook/assets/image%20%281%29.png)

#### Public Route Table

* Associate the 10.0.1.0 with the public route table and becomes as public subnet

#### Private Route Table

* Associate the 10.0.3.0/24 subnet with the private route table and becomes a private subnet

### Scenario 3A: Communicating between subnets

When subnet systems communicate with each other:

1. The 10.0.3.0/24 private subnet request goes out to the router
2. The router checks the route table ASSOCIATED with that subnet FIRST \(this is always true\)
3. It sees that the 10.0.3.48 request is within the specified range 10.0.0.0/16 and is allowed to communicate within local \(10.0.0.0/16\) components in the VPC, in this case 10.0.1.35

### Scenario 3B: Communicating between subnets

When subnet systems communicate with each other:

1. The 10.0.3.48 system is requesting for an IP that is outside, 52.19.1.4
2. This will be denied because it is not specified in the rule entries on its associated private route table
3. Conclusion: this subnet is private only because it's not allowed to communicate with external sources.

![](../../../.gitbook/assets/image%20%2866%29.png)

## III. ENABLE PUBLIC 

EC2 should also have a public IP address associated with it.

![](../../../.gitbook/assets/image%20%2881%29.png)



#### Public Route Table

* Associate the EC2 with an elastic IP address.  Diagram above shows that from any ip address \(0.0.0.0\) we can access the Internet Gateway

#### Private Route Table

* Even if an Elastic IP address was associated with 10.0.3.48, it would not connect to the internet because the route table associated with it doesn't not specify such thing

## NAT GATEWAY

NAT Gateway is used when you do NOT want inbound traffic to your system, but you need outbound, i.e. requesting web server updaes.

![](../../../.gitbook/assets/image%20%2841%29.png)

* The private route now has an entry entry from any sources.
* The NAT checks with the route table associated w/then then forwards the request from 10.0.3.48 out externally.
* NAT does allow for the request's response from the external sources because it keeps tracks for the request, port and associated source 

## IV. ENABLE VPC ENDPOINTS

![](../../../.gitbook/assets/image%20%2851%29.png)

## V. ENABLE VPC ENDPOINTS

![](../../../.gitbook/assets/image%20%2861%29.png)


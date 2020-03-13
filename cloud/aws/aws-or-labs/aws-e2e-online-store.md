# AWS E2E: Online Store

![](../../../.gitbook/assets/image%20%28101%29.png)

## I. CREATE VPC

1. Create a VPC JuliesStore
   1. Create a 2 public and 2 private subnets Julie-Public-Subnet-1a \(1A, 1B, 1C, 1D, 10.10.1/2/3/4.0/24\)
2. Create Internet Gateway: Julie-IGW
   1. attach it to the VPC
3. Create a Private/Public Route Table: Julie-Private-RT, Julie-Public-RT
4. Create NAT Gateway: specify the subnet \(usually in public\): 1A. This requires an elastic IP
   1. [Attach NAT Gateway](https://youtu.be/E-WdMk7_IQo?t=912) to the route table to your private subnets  so the instances in there have access to the internet
      1. In the Private RT &gt; Routes &gt; Destination include the local subnet which includes the private subnets 10.10.0.0/16 and 0.0.0.0/0 select the NAT Gateway from the drop-down
      2. Associate private subnets using the Subnets Associations tab \(1C, 1D\)
   2. Add internet Gateway to the public Route Table
      1. in Routes add 0.0.0.0/0 and select the Internet Gateway

![4.1.1](../../../.gitbook/assets/image%20%2896%29.png)

![](../../../.gitbook/assets/image%20%28112%29.png)

## II. CREATE EC2 INSTANCE - Web Server

* Assign it to public subnet 1A
* Include public IP Address
* For Tags Name: Webserver

![](../../../.gitbook/assets/image%20%289%29.png)

### Create a security group: Webserver-SecurityGroup

![](../../../.gitbook/assets/image%20%2819%29.png)

### 

### Create IAM Roles

1. IAM &gt; Roles &gt; EC2 &gt; copy EC2 Use Case &gt; Search for s3fu.  Name: S3\_Full-Access
2. Attach the IAM role to the EC2 instance: Instance &gt; Actions &gt; Instance Settings &gt; Attach/Replace IAM Role &gt; Select S3\_Full-Access

## III. ENABLE SNS 

SNS &gt; Get Started &gt; Topics &gt; Create New Topic: "L1-Support-Team." 

Create a subscription. From Topics, for the new topic created click create Create Subscription &gt; Protocol: email &gt; provide an email address

\*\* Whenever using this SNS topic I will get an email notification  



## IV. CREATE DB

1. Create Security Group for RDS-SG and webserver
   * NETWORK & SECURITY &gt; Security Groups &gt; Create Security Group

ONLY servers that have this security group attached are the only servers that will have access my database

![](../../../.gitbook/assets/image%20%2832%29.png)

### 2. Create your DB Services

Services &gt; Databases &gt; RDS &gt; Get Started &gt; MySQL &gt; Select Dev/Test - MySQL

* note if you select Production it will do multi-edging

![](../../../.gitbook/assets/image%20%2835%29.png)

![](../../../.gitbook/assets/image%20%2887%29.png)



## V. CREATE LOAD BALANCER

### Using Classic Load Balancer

![](../../../.gitbook/assets/image%20%2818%29.png)

* Name: Julie-ELB
* Under Julie-VPC
* We are opening port 80 in the ELB security group
* Should be spread across public subnets only

### Assigning Security Groups

* ELB-SG
* We are only opening port 80

![](../../../.gitbook/assets/image%20%28117%29.png)

### Configuring Health Check

![](../../../.gitbook/assets/image%20%282%29.png)



Pending steps:

{% embed url="https://youtu.be/E-WdMk7\_IQo?t=1743" %}






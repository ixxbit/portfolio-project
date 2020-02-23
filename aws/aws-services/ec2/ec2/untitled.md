# Untitled

For each rule, you specify the following: 

• Protocol: The protocol to allow. The most common protocols are 6 \(TCP\) 17 \(UDP\), and 1 \(ICMP\). 

• Port range: For TCP, UDP, or a custom protocol, the range of ports to allow. You can specify a single port number \(for example, 22\), or range of port numbers \(for example, 7000-8000\). 

• ICMP type and code: For ICMP, the ICMP type and code. 

• Source or destination: The source \(inbound rules\) or destination \(outbound rules\) for the traffic. Specify one of these options: 

• [An individual IPv4 address.](https://en.wikipedia.org/wiki/Reserved_IP_addresses) You must use the /32 prefix length; for example, 203.0.113.1/32. 

• An individual IPv6 address. You must use the /128 prefix length; for example 2001:db8:1234:1a00::123/128.

 • A range of IPv4 addresses, in CIDR block notation, for example, 203.0.113.0/24.

• A range of IPv6 addresses, in CIDR block notation, for example, 2001:db8:1234:1a00::/64. 

• The prefix list ID for the AWS service; for example, pl-1a2b3c4d. For more information, see Gateway VPC Endpoints in the Amazon VPC User Guide. 

• Another security group. This allows instances associated with the specified security group to access instances associated with this security group. This does not add rules from the source security group to this security group. You can specify one of the following security groups: 

* The current security group 
* A different security group for the same VPC 
* A different security group for a peer VPC in a VPC peering connection 

\(Optional\) Description: You can add a description for the rule; for example, to help you identify it later. A description can be up to 255 characters in length. Allowed characters are a-z, A-Z, 0-9, spaces, and .\_-:/\(\)\#,@\[\]+=;{}!$\*.


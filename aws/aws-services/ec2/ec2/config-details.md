# Config Details

## To create and configure your security group

 Decide who may access your instance, for example, a single computer or all trusted computers on a network. For this tutorial, you can use the public IP address of your computer. To find your IP address, use the checkip service from AWS3 or search for the phrase "what is my IP address" in any Internet search engine. If you are connecting through an ISP or from behind your firewall without a static IP address, you will need to find the range of IP addresses used by client computers. If you don't know this address range, you can use 0.0.0.0/0 for this tutorial. However, this is unsafe for production environments because it allows everyone to access your instance using SSH.

```
$ checkip service f
```

{% hint style="info" %}
[FAQ details](../../../../aws-common-config-tasks/faq.md#what-is-a-security-group-for-ec-2) 
{% endhint %}



Once you're strong enough, save the world:

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}




# ifconfig



## ifconfig command in Linux with Examples

**ifconfig**\(interface configuration\) command is used to configure the kernel-resident network interfaces. It is used at the boot time to set up the interfaces as necessary. After that, it is usually used when needed during debugging or when you need system tuning. Also, this command is used to assign the IP address and netmask to an interface or to enable or disable a given interface.

**Syntax:**

```text
ifconfig [...OPTIONS] [INTERFACE]
```

**Options:**  
  


* **-a :** This option is used to display all the interfaces available, even if they are down.

  **Syntax:**

  ```text
  ifconfig -a
  ```

  **Output:** 

  ![](https://media.geeksforgeeks.org/wp-content/uploads/Screenshot-from-2019-01-21-09-50-12.png)

* **-s :** Display a short list, instead of details.

  **Syntax:**

  ```text
  ifconfig -s
  ```

  **Output:**

  ![](https://media.geeksforgeeks.org/wp-content/uploads/Screenshot-from-2019-01-21-09-53-19.png)

* **-v :** Run the command in verbose mode – log more details about execution.

  **Syntax:**

  ```text
  ifconfig -v
  ```

  **Output:**

  ![](https://media.geeksforgeeks.org/wp-content/uploads/Screenshot-from-2019-01-21-09-56-23.png)

* **up :** This option is used to activate the driver for the given interface.

  **Syntax:**

  ```text
  ifconfig interface up
  ```

* **down :** This option is used to deactivate the driver for the given interface.

  **Syntax:**

  ```text
  ifconfig interface down
  ```

* **add addr/prefixlen :** This option is used to add an IPv6 address to an interface.

  **Syntax:**  
  


  ```text
  ifconfig interface add addr/prefixlen
  ```

* **del addr/prefixlen :** This option is used to remove an IPv6 address to an interface.

  **Syntax:**

  ```text
  ifconfig interface del addr/prefixlen
  ```

* **\[-\]arp :** This option is used to enable/disable the use of ARP protocol on an interface.

  **Syntax:**

  ```text
  ifconfig interface [-]arp
  ```

* **\[-\]promisc :** This option is used to enable/disable the promiscuous mode on an interface. If it is selected, all the packets on the network will be received by the interface.

  **Syntax:**

  ```text
  ifconfig interface [-]promisc
  ```

* **\[-\]allmulti :** This option is used to enable/disable all-multicast mode for an interface. If it is selected, all the multicast packets will be received by the interface.

  **Syntax:**

  ```text
  ifconfig interface [-]allmulti
  ```

* **mtu N :** The user uses this parameter to set the Maximum Transfer Unit\(MTU\).

  **Syntax:**

  ```text
  ifconfig interface [-]allmulti
  ```

* **–help :** Display help related to ifconfig command.

  **Syntax:**

  ```text
  ifconfig --help
  ```

  **Output:**

  ![](https://media.geeksforgeeks.org/wp-content/uploads/Screenshot-from-2019-01-21-10-27-45.png)


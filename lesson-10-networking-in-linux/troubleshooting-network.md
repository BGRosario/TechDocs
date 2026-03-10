# Troubleshooting Network

### Verify Connectivity:

* Use ping to verify connectivity
* ping6 \[address] for IPv6

{% hint style="info" %}
if is link-local addresses, you must specify the NIC name in the command
{% endhint %}

***

### Troubleshooting Routing

* ip route - prints the routing table&#x20;
* ip -6 route - shows the IPv6 routing table
* tracepath _example.com_ shows the entire networking path&#x20;
* tracepeth6 _example.com_ does the same for an IPv6 (if existing)
* **ss** is used to analyze socket statistics
  * **ss -tu**
  * **ss -tuna**
  * **ss -tunap**

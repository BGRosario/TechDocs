# Managing Persistent Network Configuration with nmcli

On the exam, you want to be fast, not be delayed by using nmcli. Use nmtui instead, but here are some useful things with nmcli:&#x20;

```bash
nmcli con show - shows current connections 
nmcli dev status - shows current network devices 
nmcli con add con-name MYNEWCONNECTION ifname ens33 ipv4.addresses 10.0.0.10/24
ipv4.gateway 10.0.0.1 ipv4.method manual type ethernet - will add a new connection
```

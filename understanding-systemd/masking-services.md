# Masking Services

With Systemctl, you can mask services so they are not enabled by other administrators, since some units cannot work simultaneously on the same server.&#x20;

```
systemctl mask [UNIT]
systemctl unmask removes the unit mask
```

The command will link the unit to the `/dev/null` which ensures that it cannot be started.&#x20;






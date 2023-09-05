## example usage
```
pcs resource create virtual_ip ocf:heartbeat:IPaddr2 ip=1.1.1.1 nic=ens3 cidr_netmask=32
pcs resource create floating_ip ocf:hetzner:floating_ip ip=1.1.1.1 api_token=super_long_and_pretty_token
pcs resource group add IP virtual_ip floating_ip
pcs constraint colocation add floating_ip virtual_ip INFINITY
pcs constraint order virtual_ip then floating_ip
pcs constraint location IP prefers node master-node
```

**Important! jq must be the latest version**
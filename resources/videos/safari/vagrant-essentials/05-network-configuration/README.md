# Forwarded ports
- good option if only a couple of ports should be exposed
```
config.vm.network "forwarded_port", host: 8080, guest: 80
```
```bash
cd ubuntu16/forward
vagrant up
telnet localhost 8080
```

# Private Network
- all guests can access each other if on same subnet
- guests not accessible from outside the host
- good option if lots of ports and only accessed from host
### DHCP
```
config.vm.network "private_network", type: "dhcp"
```
```bash
vagrant up

# note the private IP range in use:
ifconfig -a | grep -A 2 vboxnet2

# note the assigned IP
vagrant ssh -- ifconfig | grep -A 1 eth1
```

### Static IP
```
config.vm.network "private_network", ip: "172.16.0.10"
```

# Public Network
- good option if you want to mimic a physical host connected to the network
### DHCP
```
config.vm.network "public_network"

# specify physical connection
config.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)"
```

### Static IP
```
config.vm.network "public_network", ip: "10.0.0.200"
```

# Using Multiple Network Options
- Mix forwarded ports and public networks
- Limited to number of network cards



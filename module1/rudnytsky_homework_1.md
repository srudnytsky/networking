# command 1
```bash
ip -a
```

### command output

srudnytsky@Trinity:~/networking/networking$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet 10.255.255.254/32 brd 10.255.255.254 scope global lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:15:5d:6b:86:a4 brd ff:ff:ff:ff:ff:ff
    inet 172.25.51.69/20 brd 172.25.63.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::215:5dff:fe6b:86a4/64 scope link 
       valid_lft forever preferred_lft forever

### understanding command output

- [x] Interface - eth0
- [x] Connection type - Ethernet
- [x] MAC-address - 00:15:5d:6b:86:a4
- [x] Ip address - 172.25.51.69
- [x] Subnet - 255.255.240.0 or /20
- [x] Gateway - unknown
- [x] Broadcast address - 172.25.63.255
- [x] Count of possible hosts - 4094

# comand 2
```bash
ip -r
```

### command output

srudnytsky@Trinity:~/networking/networking$ ip r
default via 172.25.48.1 dev eth0 proto kernel 
172.25.48.0/20 dev eth0 proto kernel scope link src 172.25.51.69 

### understanding command output

[x] Route by default - default
[x] Gateway - 172.25.48.1
[x] Interface - eth0
[x] Source IP - 172.25.48.0/20
[x] Route protocol - kernel

# command 3
```bash
curl ifconfig.io
```

### command output

srudnytsky@Trinity:~/networking/networking$ curl ifconfig.io
188.163.8.75


### explanation

The routing table determines where the operating system sends network packets. The default route sends packets to other networks through gateway `172.25.48.1` via interface `eth0`. The second route represents the directly connected network `172.25.48.0/20`, with `172.25.51.69` as the source IP address.

The `proto kernel` parameter indicates that the routes are associated with the Linux kernel; it does not mean the IP address was obtained through DHCP. Since Linux is running in WSL, gateway `172.25.48.1` belongs to the WSL virtual network and may differ from the physical home router's IP address.

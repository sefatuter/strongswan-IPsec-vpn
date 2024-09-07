# strongswan-IPsec-vpn

1. 

2. Set up firewalld configurations on each clients. 

```
sudo firewall-cmd --permanent --add-port=80/tcp
sudo firewall-cmd --permanent --add-port=500/udp
sudo firewall-cmd --permanent --add-port=4500/udp
sudo firewall-cmd --permanent --add-masquerade
sudo firewall-cmd --reload
```

Extra:
```
nmcli d
nmtui
```

3.Install& Configure Strongswan on each clients.

```
dnf install epel-release
dnf update
dnf install strongswan strongswan-charon-nm
sudo yum install libreswan
```

```
client1: 192.168.56.104 (private ip) (enp0s3), 192.168.58.5 (public ip) (enp0s8)
client2: 192.168.57.5 (private ip) (enp0s3), 192.168.58.6 (public ip) (enp0s8)
```

IP Forwarding Configuration
```
nano /etc/sysctl.conf

net.ipv4.ip_forward = 1
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.send_redirects = 0

sysctl -p /etc/sysctl.conf
```


```
client1: 192.168.56.101(private) (enp0s3), 192.168.58.101(public) (enp0s8)
client2: 192.168.57.102(private) (enp0s3), 192.168.58.102(public) (enp0s8)
	
server1: 192.168.56.102
server2: 192.168.57.3
```

```
ip addr | grep "192.168.56"
```

```
root@server1:~ ssh root@192.168.56.102
root@server2:~ ssh root@192.168.57.3

root@strongswan1:~ ssh centos1@192.168.58.101
root@strongswan2:~ ssh centos2@192.168.58.102
```

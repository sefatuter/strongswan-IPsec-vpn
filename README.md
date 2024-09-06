# strongswan-IPsec-vpn

```
dnf install epel-release
dnf update
dnf install strongswan strongswan-charon-nm
sudo yum install libreswan
```


```
sudo firewall-cmd --permanent --add-port=80/tcp
sudo firewall-cmd --permanent --add-port=500/udp
sudo firewall-cmd --permanent --add-port=4500/udp
sudo firewall-cmd --permanent --add-masquerade
sudo firewall-cmd --reload
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

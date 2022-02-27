openvpn-install
==============

Ref:
https://www.cyberciti.biz/faq/centos-8-set-up-openvpn-server-in-5-minutes/
https://github.com/angristan/openvpn-install

sudo dnf update
sudo yum update

## [-- eth0 is server interface with IPv4/IPv6 --] ##

## [-- tun0 is OpenVPN interface ##

## [-- 10.8.0.0/24 sub/net for OpenVPN --] ##

## [-- ADJUST VALUES AS PER YOUR SET UP WHEN TYPING THE FOLLOWING COMMANDS --] ##

## A note about FirewallD on CentOS 8 ##
By default, FirewallD will block access to UDP/1194, and the above script is not compatible with iptables rules on your OpenVPN server. First, find out if firewalld active or not on the server, run:

```bash
sudo firewall-cmd --get-active-zones
sudo firewall-cmd --zone=trusted --add-interface=tun0
sudo firewall-cmd --permanent --zone=trusted --add-interface=tun0
sudo firewall-cmd --permanent --add-service openvpn
sudo firewall-cmd --permanent --zone=trusted --add-service openvpn
sudo firewall-cmd --reload
sudo firewall-cmd --list-services --zone=trusted
sudo firewall-cmd --add-masquerade
sudo firewall-cmd --add-masquerade --permanent
sudo firewall-cmd --query-masquerade
```

# note eth0 is where servers public ipv4/ipv6 assinged #

Run one of two command
```
sudo firewall-cmd --permanent --direct --passthrough ipv4 -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```
```
sudo firewall-cmd --permanent --direct --passthrough ipv4 -t nat -A POSTROUTING -s 10.8.0.0/24 -o ens33 -j MASQUERADE
```

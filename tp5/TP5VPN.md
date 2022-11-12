ssh rocky@51.68.70.139
51.68.70.139/32
sudo dnf install nano

sur mon terminal ssh-keygen -b 4096 

ce qui me donne une clé publique que j'enregistre dans un nano sur le terminal du vpn

nano ~/.ssh/authorized_keys

clé pub

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDaVZP4LkzTNetMS/y+BGGdmkek0X6jFI+5R/gF0sF0pQDNv03VQTJk1uPPrUtipCaFlpKLcjH4/odcXX5S/OKLXYq3WRwE4cj2Pgs5Xrn9FQZHSDPfuVYmTjPfZF8NrPw8p21rwMGJ9puxMdOSxJWqn2tCGYo4s25WQkGas7V+DM7tEeW0wS+3rviTNSuJIhiyhdtxuDwoaDdvqSzUAiOjSc4r5wYUOD1GJPzB8ZmOnqmIiMCpX1ig27HTSAiTIUBAlLsS1x5gV7zH80OvYWYNsiIw7DAFNEXpGWbaGhWE/7iTMg+VtdGGoZd5m5LDaDiMAMsx0BjS/12CM818d0Jc0pRtjQnQQnc7ve7nV8E2prMyjagv3oq36YynfmSze3gUp67akgTiPi8QeutjrZdKbmq9lWV0wCdjyCgv9/UrU4GZK7XniMqibQYa1wEmLNodfN+A0nT6Xa4XH6+PbNmIt3kQOOjPoirCPKohTAgquk2zH4NMP2LvWhz9I1DierU7HXqjRfGmIeck9E3Z4G5ALh/o5laLllcHmwH8QatjITRRDzOs8HfPTDYmPCp3CLQPaCAl928PQBKg5uNGvPwInLA6gfE45RVsKffFmwRxGZaBx4Yh7TsCArgbr+Z0C6GQpEb0cjFcgko140c+tQjJ750/P1Ekh7fDd5OV8Ok6Qw== ranvin@Timothee


usermod -aG wheel rocky

dnf install firewalld -y

systemctl start firewalld

systemctl status firewalld

set mark: ...skipping...
● firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2022-11-11 11:07:14 UTC; 21s ago
     Docs: man:firewalld(1)
 Main PID: 6796 (firewalld)
    Tasks: 2 (limit: 10836)
   Memory: 24.9M
   CGroup: /system.slice/firewalld.service
           └─6796 /usr/libexec/platform-python -s /usr/sbin/firewalld --nofork --nopid


firewall-cmd --permanent --add-service=http

firewall-cmd --reload

sudo dnf install elrepo-release epel-release

sudo dnf install kmod-wireguard wireguard-tools

wg genkey | sudo tee /etc/wireguard/private.key

sudo chmod go= /etc/wireguard/private.key

/etc/ssh/sshd_config

 sudo nano / etc / ssh / sshd_config 
 PermitRootLogin no
sudo -s
 passwd --lock root

 sudo -d passwd rocky

 [rocky@vps-88175d19 etc]$ sudo dnf install kmod-wireguard wireguard-tools
Last metadata expiration check: 2:08:54 ago on Fri 11 Nov 2022 12:05:50 PM UTC.
Error:
 Problem: cannot install the best candidate for the job
  - nothing provides kernel >= 4.18.0-425.3.1.el8 needed by kmod-wireguard-7:1.0.20220627-3.el8_7.elrepo.x86_64
(try to add '--skip-broken' to skip uninstallable packages or '--nobest' to use not only best candidate packages)

sudo dnf install kmod-wireguard wireguard-tools --nobest

MBvZ1HAxH5942GsjTDEQ9zAHfWgdfP45Cd3E++7N6kw= -> clé privé 

jttDVI4nSHvRVBtPvXkRQlbLV3u7fKcb6OO8hxtNCzs= -> clé public 

sudo nano /etc/sysconfig/network-scripts/ ifcfg-eth0
10.8.0.1/24 adresse ip utilisée

le fichier initial dans ifcfg-eth0
BOOTPROTO=dhcp
DEVICE=eth0
HWADDR=fa:16:3e:ed:dd:dd
MTU=1500
ONBOOT=yes
TYPE=Ethernet
USERCTL=no


mon fichier
DEVICE=eth0

BOOTPROTO=static
ONBOOT=yes

IPADDR=10.8.0.1
NETMASK=255.255.255.0


51.68.70.139 ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBGuab3vyat591AJSrxTuhX4xsulBZUcsCuAv2dNFIi56tAXZQ36RSO7MBIkVU8mnSxgqBgzmlDVTaDHaMP44zHE=
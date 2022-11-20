```ssh rocky@51.68.70.139```

```sudo dnf install nano```

```sur mon terminal ssh-keygen -b 4096``` 

>ce qui me donne une clé publique que j'enregistre dans un nano sur le terminal du vpn

```nano ~/.ssh/authorized_keys```

>clé pub

```ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDjkVSpFGRCC66BjMLIxWoF+eYk6/DPmjpLsMTA6OLegHAq+IZA2LwaiO64lJEyN2wZtefq3agjcziQEuDPw6NlBsh22ekUl8SEkXReUXE3KGsWaf69DR1ss27+DQ1lKzCh8XtVmVIh7bywrEH5DznOJnlCGihiZ+5ivRZ8dtZy3uorH4N8E60oQWRdsi5YhvzimcfH79FZJNbg4yhDjMoJ3jn3SsWjNYNnH+G15vlGw3j7Z2Czq41LXp0uLrHo7V9UYp43o2b62q58Ssxmer5ad/8lXRFc4KfuWOZBntiq2CqahaLTYncJBVgDj+BRiP6CRvk+0ijhN5BsABQeGkHccW6EZkPdg5RQU7LS2vP4cDEMoJDjguTpiM7Jk67r3oXdKwKMTZF3EmhqJIxO4wXiLNcjTbQcw5lu4Qa9pWSDwsg8e1zgsB2Z33bj88szaRefzvukEfeC/m+ySwgrtf6B2HVunl/zo3nwqFgZQfAxjuA4wR3+Jn13rQZHod82wbOvzu+x6obSKx8mlgzxaClwYI33ftWYtZoQDhmcHib4XMivJjSLLDT/0mo4HTaQtFY2DAqeh3daPDdILtrnllGJmT1D9/tGa6c/uMS/1UqNl9bXD+WHVma3RCsubdJ0dlRRgFvKcwFvz79+Lcq4OQu+g3c8qaprbjPKrK362N9qGw== ranvin@Timothee```

```sudo su```

```usermod -aG wheel rocky```

``` dnf install firewalld -y```

```systemctl start firewalld```

```systemctl status firewalld```

```sudo dnf install elrepo-release epel-release```

```sudo dnf install kmod-wireguard wireguard-tools```

```wg genkey | sudo tee /etc/wireguard/private.key```
```sudo chmod go= /etc/wireguard/private.key```


>set mark: ...skipping...
● firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2022-11-11 11:07:14 UTC; 21s ago
     Docs: man:firewalld(1)
 Main PID: 6796 (firewalld)
    Tasks: 2 (limit: 10836)
   Memory: 24.9M
   CGroup: /system.slice/firewalld.service
           └─6796 /usr/libexec/platform-python -s /usr/sbin/firewalld --nofork --nopid         


>firewall-cmd --permanent --add-service=http

>firewall-cmd --reload


```clé privé wg=   4Pc8+RK30KDE+ZEYRZpd1/Li3bi94BwlNlsvSTdReXU=```

```clé pub wg = 4Gv0Ft5dj/BjgrzzhFlKsnE57T6vPZYbLf8hA7SkpzU=```

```10.8.0.1/24```

```sudo vi /etc/wireguard/wg0.conf```

```shift zz```

>/etc/wireguard/wg0.conf
[Interface]
PrivateKey = 4Pc8+RK30KDE+ZEYRZpd1/Li3bi94BwlNlsvSTdReXU=
Address = 10.8.0.1/24, 
ListenPort = 51820
SaveConfig = true

```sudo nano /etc/sysctl.conf```

```net.ipv4.ip_forward=1```

```dnf install firewalld -y```

```systemctl start firewalld```

```systemctl status firewalld```

>See system logs and 'systemctl status firewalld.service' for details.
[rocky@vps-823031fd ~]$ sudo systemctl start firewalld
[rocky@vps-823031fd ~]$ systemctl status firewalld
● firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2022-11-20 18:02:49 UTC; 45s ago
     Docs: man:firewalld(1)
 Main PID: 137517 (firewalld)
    Tasks: 2 (limit: 10836)
   Memory: 25.5M
   CGroup: /system.slice/firewalld.service
           └─137517 /usr/libexec/platform-python -s /usr/sbin/firewalld --nofork --nopid

>Nov 20 18:02:48 vps-823031fd.vps.ovh.net systemd[1]: Starting firewalld - dynamic firewall daemon...
Nov 20 18:02:49 vps-823031fd.vps.ovh.net systemd[1]: Started firewalld - dynamic firewall daemon.
Nov 20 18:02:49 vps-823031fd.vps.ovh.net firewalld[137517]: WARNING: AllowZoneDrifting is enabled. This is considered an insecu>
lines 1-13/13 (END)

```sudo firewall-cmd --zone=public --add-port=51820/udp --permanent```

```sudo firewall-cmd --zone=internal --add-interface=wg0 --permanent```

```sudo firewall-cmd --zone=public --add-rich-rule='rule family=ipv4 source address=10.8.0.0/24 masquerade' --permanent```

```sudo firewall-cmd --reload```

```sudo firewall-cmd --zone=public --list-all```

>public (active)
  target: default
  icmp-block-inversion: no
  interfaces: eth0
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 51820/udp
  protocols:
  forward: no
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
        rule family="ipv4" source address="10.8.0.0/24" masquerade

```sudo firewall-cmd --zone=internal --list-interfaces```


```wg0```

```sudo systemctl enable wg-quick@wg0.service```

```Created symlink /etc/systemd/system/multi-user.target.wants/wg-quick@wg0.service → /usr/lib/systemd/system/wg-quick@.service.```

```sudo systemctl start wg-quick@wg0.service```

```sudo systemctl status wg-quick@wg0.service```

>● wg-quick@wg0.service - WireGuard via wg-quick(8) for wg0
   Loaded: loaded (/usr/lib/systemd/system/wg-quick@.service; enabled; vendor preset: disabled)
   Active: active (exited) since Sun 2022-11-20 18:35:46 UTC; 10s ago
     Docs: man:wg-quick(8)
           man:wg(8)
           https://www.wireguard.com/
           https://www.wireguard.com/quickstart/
           https://git.zx2c4.com/wireguard-tools/about/src/man/wg-quick.8
           https://git.zx2c4.com/wireguard-tools/about/src/man/wg.8
  Process: 4776 ExecStart=/usr/bin/wg-quick up wg0 (code=exited, status=0/SUCCESS)
 Main PID: 4776 (code=exited, status=0/SUCCESS)

>Nov 20 18:35:46 vps-823031fd.vps.ovh.net systemd[1]: Starting WireGuard via wg-quick(8) for wg0...
Nov 20 18:35:46 vps-823031fd.vps.ovh.net wg-quick[4776]: [#] ip link add wg0 type wireguard
Nov 20 18:35:46 vps-823031fd.vps.ovh.net wg-quick[4776]: [#] wg setconf wg0 /dev/fd/63
Nov 20 18:35:46 vps-823031fd.vps.ovh.net wg-quick[4776]: [#] ip -4 address add 10.8.0.1/24 dev wg0
Nov 20 18:35:46 vps-823031fd.vps.ovh.net wg-quick[4776]: [#] ip link set mtu 1420 up dev wg0
Nov 20 18:35:46 vps-823031fd.vps.ovh.net systemd[1]: Started WireGuard via wg-quick(8) for wg0.

```sudo dnf install elrepo-release epel-release```

```sudo dnf install kmod-wireguard wireguard-tools```

```wireguard windows 11 clé pub 1iC5nwZfbQ8MNQ+ssIat0CUn8b7a0N1qqeEWta8MPCY=```

```PrivateKey = gMGJ+VsMD9s0wg4KpxJtIJbNImpZDKwb/qs8mRQO/lw=```

```sudo wg set wg0 peer 1iC5nwZfbQ8MNQ+ssIat0CUn8b7a0N1qqeEWta8MPCY= allowed-ips 10.8.0.2```

```sudo wg```

>[rocky@vps-823031fd ~]$ sudo wg
interface: wg0
  public key: 4Gv0Ft5dj/BjgrzzhFlKsnE57T6vPZYbLf8hA7SkpzU=
  private key: (hidden)
  listening port: 51820

>peer: 1iC5nwZfbQ8MNQ+ssIat0CUn8b7a0N1qqeEWta8MPCY=

```sudo wg-quick up wg0```

```ping -c 1 10.8.0.1```

>[Interface]
PrivateKey = gMGJ+VsMD9s0wg4KpxJtIJbNImpZDKwb/qs8mRQO/lw=
Address = 10.8.0.2/24
[Peer]
PublicKey = 4Gv0Ft5dj/BjgrzzhFlKsnE57T6vPZYbLf8hA7SkpzU=
AllowedIPs = 10.8.0.0/24
Endpoint = 51.68.70.139:51820

 ```sudo nano /etc/ssh/sshd_config```

>PermitRootLogin no



Adresse mac de john 08:00:27:81:14:4f
adresse mac de marcel 08:00:27:30:db:7b

ip neigh show 10.3.1.12 adresse mac 08:00:27:30:db:7b
ip neigh show 10.3.1.11
mac 08:00:27:81:14:4f

1 requête arp 08:00:27:48:1e:96 john 08:00:27:81:14:4f  10.3.1.254 
3 requête arp 08:00:27:81:14:4f routeur 08:00:27:81:14:4f 10.3.1.11
5 requête arp 08:00:27:30:db:7b marcel 08:00:27:30:db:7b 10.3.2.254
6 requête arp 08:00:27:30:db:7b routeur 08:00:27:01:41:0d 10.3.2.12
8 ping 10.3.1.11 john  08:00:27:81:14:4f 10.3.1.254 
9 pong 10.3.1.254 routeur 08:00:27:48:1e:96 10.3.1.11
10 ping 10.3.2.12 marcel 08:00:27:30:db:7b 10.3.2.254
11 pong 10.3.2.254 routeur 08:00:27:01:41:0d 10.3.2.12 



ping john 10.3.1.11 08:00:27:81:14:4f 8.8.8.8 08:00:27:48:1e:96
pong serveur 8.8.8.8 08:00:27:48:1e:96 10.3.1.11 08:00:27:81:14:4f


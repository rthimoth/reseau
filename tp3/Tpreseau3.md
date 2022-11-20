1
>ip neighbour de chaque coté pour afficher les adresses MAC des vm et passerelle

>Adresse mac de john 08:00:27:81:14:4f
>adresse mac de marcel 08:00:27:30:db:7b

>ip neigh show marcel 10.3.1.12 adresse mac 08:00:27:30:db:7b

>ip neigh show john 10.3.1.11 mac 08:00:27:81:14:4f



2
 >sudo tcpdump -i enp0s8 -c 100 -w mon_fichier.pcap not port 22

>sudo ip neigh flush all 
 II routage
 sudo nano /etc/sysconfig/network-scripts/
 et sudo nano /etc/sysconfig/network/
 sudo systemctl restart NetworkManager

 >sudo ip neigh flush all 

>sudo firewall-cmd --add-masquerade --zone=public --permanent

>1 requête arp 08:00:27:48:1e:96 john 08:00:27:81:14:4f  10.3.1.254 
3 requête arp 08:00:27:81:14:4f routeur 08:00:27:81:14:4f 10.3.1.11
5 requête arp 08:00:27:30:db:7b marcel 08:00:27:30:db:7b 10.3.2.254
6 requête arp 08:00:27:30:db:7b routeur 08:00:27:01:41:0d 10.3.2.12
8 ping 10.3.1.11 john  08:00:27:81:14:4f 10.3.1.254 
9 pong 10.3.1.254 routeur 08:00:27:48:1e:96 10.3.1.11
10 ping 10.3.2.12 marcel 08:00:27:30:db:7b 10.3.2.254
11 pong 10.3.2.254 routeur 08:00:27:01:41:0d 10.3.2.12 


3 Accés internet


>ping john 10.3.1.11 08:00:27:81:14:4f 8.8.8.8 08:00:27:48:1e:96
pong serveur 8.8.8.8 08:00:27:48:1e:96 10.3.1.11 08:00:27:81:14:4f


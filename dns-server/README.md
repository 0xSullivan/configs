## Installing BIND on DNS Servers

    sudo apt-get update
    sudo apt-get install bind9 bind9utils bind9-doc

## Config Files:
 - /etc/default/bind9
 - /etc/bind/named.conf.options
 - /etc/bind/named.conf.local
 - /etc/bind/zones/db.mmdmst.ir
---
	sudo systemctl restart bind9
	sudo named-checkconf
	sudo ufw allow Bind9

	Скрины ip на уст-вах в СКРИНЫ
	Systemctl restart networking
	Timedatectl set-timezone EuropeMoscow
	
	ISP - iptables -t nat -A POSTROUTING -s 0.0.0.0/0 -o ens192 -j MASQUERADE
		Iptables-save > /etc/iptables/rules.v4
		
	FW - Nano /etc/resolv.conf
		200.100.200.254
		Apt install iptables*
		Nano /etc/sysctl.conf (24) -> sysctl -p (ctroka)
		
	SRV-1, SRV-2 - Nano /etc/resolv.conf
			200.100.100.254
			
	FW - iptables -t nat -A POSTROUTING -s 172.20.0.0/16 -o ens192 -j MASQUERADE
		Iptables-save > /etc/iptables/rules.v4
		
DC------------------------------------------------------------------------------------------------
2 АД + юзеры + таймзона
3 ДНС зоны (Тулз - ДНС)
	ПКМ company.msk - new host 
		_____ - 200.100.200.100
		App - 200.100.200.100
		Ntp - 172.20.30.100 (SRV-1)
		Dns - 172.20.30.20 (SRV-2)
		Ntp.branch - 192.168.200.200
		Dns.branch - 192.168.200.200
		МБ ПОСЛЕ НАСТРОЙКИ срв-1 и срв-2
		FW - 172.20.20.1 (ГАЛОЧКА) 
		Reverse Lookup Zone
			172.20.20 (FW)
		DC - 172.20.10.100
		SRV-1 -172.20.30.100
		SRV-2 - 172.20.30.20
		
	ПКМ зона company.msk - пропертис - зон трансферс
	Only to the foll servers 
		Srv-1 172.20.30.100
		Srv-2 172.20.30.20
		Srv 192.168.200.200
	ПКМ зона _msdcs - пропертис - зон трансферс
	Only to the foll servers 
		Srv-1 172.20.30.100
		Srv-2 172.20.30.20
		Srv 192.168.200.200
SRV-1 DNS-----------------------------------------------------------------------------------------------------------
apt install bind9
Nano /etc/bind/named.conf.options

![Alt text](namedconf.png?raw=true "Optional Title")
![kek](https://github.com/azm4/ansible/blob/a28ac102e14fc4160ca29b71a964f1013d66dd50/A/namedconf.png)

# IPTABLES-PURO

iptables puro para firewall

iptables -F

iptables -X

iptables -t nat -F

iptables -t nat -X

iptables -t mangle -F

iptables -t mangle -X


#criando logs

iptables -I OUTPUT -j LOG

iptables -I INPUT -j LOG

iptables -I FORWARD -j LOG

#bloqueado tudo

iptables -P INPUT DROP

iptables -P FORWARD DROP

iptables -P OUTPUT DROP


#liberado icmp

iptables -I INPUT -p icmp -j ACCEPT

iptables -I OUTPUT -p icmp -j ACCEPT


#liberando consulta DNS

iptables -I OUTPUT -p udp --dport 53 -j ACCEPT

iptables -I INPUT -p udp --sport 53 -j ACCEPT

#liberando navegacao

iptables -I OUTPUT -p tcp --dport 443 -j ACCEPT

iptables -I INPUT -p tcp --sport 443 -j ACCEPT

iptables -I OUTPUT -p tcp --dport 80 -j ACCEPT

iptables -I INPUT -p tcp --sport 80 -j ACCEPT


#liberacao ALGAR

iptables -I OUTPUT -p tcp --dport 8080 -j ACCEPT

iptables -I OUTPUT -p tcp --dport 5060 -j ACCEPT

iptables -I INPUT -p tcp --sport 8080 -j ACCEPT

iptables -I INPUT -p tcp --sport 5060 -j ACCEPT

#liberando ssh

iptables -I OUTPUT -p tcp --sport 22 -j ACCEPT

iptables -I INPUT -p tcp --dport 22 -j ACCEPT



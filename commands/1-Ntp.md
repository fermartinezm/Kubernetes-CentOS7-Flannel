### Install ntp. **Only Master**
$ yum install ntp

### Configure firewalld. **Only Master**
$ firewall-cmd --add-service=ntp --permanent
<br />
$ firewall-cmd --reload

### Configure ntp. **Only Master**
vi /etc/ntp.conf

#You have to comment the lines
<br />
#server 0.centos.pool.ntp.org iburst
<br />
#server 1.centos.pool.ntp.org iburst
<br />
#server 2.centos.pool.ntp.org iburst
<br />
#server 3.centos.pool.ntp.org iburst

#You have to add the lines (Spain). If you are in other country look for a proper ntp server
<br />
server 1.es.pool.ntp.org
<br />
server 2.europe.pool.ntp.org
<br />
server 3.europe.pool.ntp.org

#You have to add the lines
<br />
restrict <IP_MINION1> mask 255.255.255.0 nomodify notrap
<br />
restrict <IP_MINION2> mask 255.255.255.0 nomodify notrap
<br />
#Add more minions if you have more

### Restart and enable ntp service. **Only Master**
$ systemctl restart ntpd
<br />
$ systemctl enable ntpd
<br />


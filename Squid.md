# INSTALL AND CONFIG SQUID ON RHEL/ CENTOS

#TO INSTALL SQUID 
   
   > yum install squid -y

#Now changes are to be made in "squid.conf" file

   > we can find squid.conf 
      cd /etc/lib/squid


enable cache dir
uncomment line 62
cache_dir ufs /var/spool/squid 2048 16 256
2048 cache size
16 sub dir under /spool/squid
256 dir under 16 dir


visible_hostname proxy.panda.demo
show error name as proxy.panda.com

squid -z = to create swap directories



[root@STM1 ~]# yum install squid

[root@STM1 ~]# cd /etc/squid/

[root@STM1 squid]# vim squid.conf
[root@STM1 squid]# systemctl status squid
● squid.service - Squid caching proxy
   Loaded: loaded (/usr/lib/systemd/system/squid.service; disabled; vendor preset: disabled)
   Active: inactive (dead)
[root@STM1 squid]# ls /var/spool/squid/
[root@STM1 squid]# squid -z 
[root@STM1 squid]# 2023/06/24 17:15:40 kid1| Set Current Directory to /var/spool/squid
2023/06/24 17:15:40 kid1| Creating missing swap directories
2023/06/24 17:15:40 kid1| /var/spool/squid exists
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/00
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/01
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/02
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/03
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/04
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/05
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/06
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/07
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/08
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/09
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/0A
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/0B
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/0C
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/0D
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/0E
2023/06/24 17:15:40 kid1| Making directories in /var/spool/squid/0F
[root@STM1 squid]# ls /var/spool/squid/
00  01  02  03  04  05  06  07  08  09  0A  0B  0C  0D  0E  0F
[root@STM1 squid]# ls /var/spool/squid/00/
00  05  0A  0F  14  19  1E  23  28  2D  32  37  3C  41  46  4B  50  55  5A  5F  64  69  6E  73  78  7D  82  87  8C  91  96  9B  A0  A5  AA  AF  B4  B9  BE  C3  C8  CD  D2  D7  DC  E1  E6  EB  F0  F5  FA  FF
01  06  0B  10  15  1A  1F  24  29  2E  33  38  3D  42  47  4C  51  56  5B  60  65  6A  6F  74  79  7E  83  88  8D  92  97  9C  A1  A6  AB  B0  B5  BA  BF  C4  C9  CE  D3  D8  DD  E2  E7  EC  F1  F6  FB
02  07  0C  11  16  1B  20  25  2A  2F  34  39  3E  43  48  4D  52  57  5C  61  66  6B  70  75  7A  7F  84  89  8E  93  98  9D  A2  A7  AC  B1  B6  BB  C0  C5  CA  CF  D4  D9  DE  E3  E8  ED  F2  F7  FC
03  08  0D  12  17  1C  21  26  2B  30  35  3A  3F  44  49  4E  53  58  5D  62  67  6C  71  76  7B  80  85  8A  8F  94  99  9E  A3  A8  AD  B2  B7  BC  C1  C6  CB  D0  D5  DA  DF  E4  E9  EE  F3  F8  FD
04  09  0E  13  18  1D  22  27  2C  31  36  3B  40  45  4A  4F  54  59  5E  63  68  6D  72  77  7C  81  86  8B  90  95  9A  9F  A4  A9  AE  B3  B8  BD  C2  C7  CC  D1  D6  DB  E0  E5  EA  EF  F4  F9  FE
[root@STM1 squid]# systemctl start squid
[root@STM1 squid]# systemctl status squid
● squid.service - Squid caching proxy
   Loaded: loaded (/usr/lib/systemd/system/squid.service; disabled; vendor preset: disabled)
   Active: active (running) since Sat 2023-06-24 17:19:13 IST; 4s ago
  Process: 5676 ExecStart=/usr/sbin/squid $SQUID_OPTS -f $SQUID_CONF (code=exited, status=0/SUCCESS)
  Process: 5670 ExecStartPre=/usr/libexec/squid/cache_swap.sh (code=exited, status=0/SUCCESS)
 Main PID: 5678 (squid)
    Tasks: 4
   CGroup: /system.slice/squid.service
           ├─5678 /usr/sbin/squid -f /etc/squid/squid.conf
           ├─5680 (squid-1) -f /etc/squid/squid.conf
           ├─5687 (logfile-daemon) /var/log/squid/access.log
           └─5688 (unlinkd)

Jun 24 17:19:13 STM1 systemd[1]: Starting Squid caching proxy...
Jun 24 17:19:13 STM1 squid[5678]: Squid Parent: will start 1 kids
Jun 24 17:19:13 STM1 squid[5678]: Squid Parent: (squid-1) process 5680 started
Jun 24 17:19:13 STM1 systemd[1]: Started Squid caching proxy.
################################################################################################################

################################################################################################################
[root@STM1 squid]# vim squid.conf
[root@STM1 squid]# systemctl restart squid

[root@STM1 squid]# cat squid.conf
#
# Recommended minimum configuration:
#

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines

acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT

#
# Recommended minimum Access Permission configuration:
#
# Deny requests to certain unsafe ports
http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports

# Only allow cachemgr access from localhost
http_access allow localhost manager
http_access deny manager

# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost

#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
acl hpcsalab src 10.10.10.0/24
acl microsoft dstdomain .microsoft.com
http_access deny microsoft hpcsalab
http_access allow hpcsalab
# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
#http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

# Squid normally listens to port 3128
http_port 3128

# Uncomment and adjust the following to add a disk cache directory.
cache_dir ufs /var/spool/squid 2048 16 256
visible_hostname proxy.panda.demo
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid

#
# Add any of your own refresh_pattern entries above these.
#
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320
################################################################################################################
$$ BLOCKED FOR NETWORK

[root@STM1 squid]# vim squid.conf

#
# Recommended minimum configuration:
#

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines

acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT

#
# Recommended minimum Access Permission configuration:
#
# Deny requests to certain unsafe ports
http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports

# Only allow cachemgr access from localhost
http_access allow localhost manager
http_access deny manager

# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost

#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
acl hpcsalab src 10.10.10.0/24
acl blocked_sites dstdomain "/etc/squid/blocked-sites.txt"
http_access deny blocked_sites hpcsalab
http_access allow hpcsalab
# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
#http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

# Squid normally listens to port 3128
http_port 3128

# Uncomment and adjust the following to add a disk cache directory.
cache_dir ufs /var/spool/squid 2048 16 256
visible_hostname proxy.panda.demo
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid

#
# Add any of your own refresh_pattern entries above these.
#
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320

[root@STM1 squid]# vim /etc/squid/blocked_sites.txt
.microsoft.com
.esakal.com
.redhat.com

[root@STM1 squid]# systemctl restart squid
################################################################################################################
$$ BLOCKED FOR PARTICULAR CLIENT
[root@STM1 squid]# vim squid.conf

#
# Recommended minimum configuration:
#

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines

acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT

#
# Recommended minimum Access Permission configuration:
#
# Deny requests to certain unsafe ports
http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports

# Only allow cachemgr access from localhost
http_access allow localhost manager
http_access deny manager

# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost

#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
acl hpcsalab src 10.10.10.0/24
acl blocked_sites dstdomain "/etc/squid/blocked-sites.txt"
http_access deny blocked_sites hpcsalab
http_access allow hpcsalab
# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
#http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

# Squid normally listens to port 3128
http_port 3128

# Uncomment and adjust the following to add a disk cache directory.
cache_dir ufs /var/spool/squid 2048 16 256
visible_hostname proxy.panda.demo
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid

#
# Add any of your own refresh_pattern entries above these.
#
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320
[root@STM1 squid]# vim squid.conf
[root@STM1 squid]# vim /etc/squid/centos7-blocked.txt
[root@STM1 squid]# cat /etc/squid/centos7-blocked.txt
.microsoft.com
.redhat.com
.facebook.com
[root@STM1 squid]# cat squid.conf
#
# Recommended minimum configuration:
#

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines

acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT

#
# Recommended minimum Access Permission configuration:
#
# Deny requests to certain unsafe ports
http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports

# Only allow cachemgr access from localhost
http_access allow localhost manager
http_access deny manager

# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost

#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
acl hpcsalab src 10.10.10.0/24
acl centos7 src 10.10.10.129
acl blocked_sites dstdomain "/etc/squid/blocked-sites.txt"
acl centos7-blocked dstdomain "/etc/squid/centos7-blocked.txt"
http_access deny centos7-blocked centos7
http_access deny blocked_sites hpcsalab
http_access allow hpcsalab
# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
#http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

# Squid normally listens to port 3128
http_port 3128

# Uncomment and adjust the following to add a disk cache directory.
cache_dir ufs /var/spool/squid 2048 16 256
visible_hostname proxy.panda.demo
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid

#
# Add any of your own refresh_pattern entries above these.
#
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320

[root@STM1 squid]# vim /etc/squid/centos7-blocked.txt

.microsoft.com
.redhat.com
.facebook.com
[root@STM1 squid]# systemctl restart squid
################################################################################################################
$$ FOR TIME PERIOD

[root@STM1 squid]# vim squid.conf
[root@STM1 squid]# cat squid.conf
#
# Recommended minimum configuration:
#

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines

acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT

#
# Recommended minimum Access Permission configuration:
#
# Deny requests to certain unsafe ports
http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports

# Only allow cachemgr access from localhost
http_access allow localhost manager
http_access deny manager

# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost

#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
acl hpcsalab src 10.10.10.0/24
acl centos7 src 10.10.10.129
acl cdac-time time A 18:00-20:00
acl cdac dstdomain .cdac.in
acl blocked_sites dstdomain "/etc/squid/blocked-sites.txt"
acl centos7-blocked dstdomain "/etc/squid/centos7-blocked.txt"
http_access deny cdac-time
http_access deny centos7-blocked centos7
http_access deny blocked_sites hpcsalab
http_access allow hpcsalab
# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
#http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

# Squid normally listens to port 3128
http_port 3128

# Uncomment and adjust the following to add a disk cache directory.
cache_dir ufs /var/spool/squid 2048 16 256
visible_hostname proxy.panda.demo
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid

#
# Add any of your own refresh_pattern entries above these.
#
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320
[root@STM1 squid]# systemctl restart squid

###################################################################################################################
$$ FOR PARTICULAR WORDS

[root@STM1 squid]# vim squid.conf
[root@STM1 squid]# cat squid.conf
#
# Recommended minimum configuration:
#

# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines

acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT

#
# Recommended minimum Access Permission configuration:
#
# Deny requests to certain unsafe ports
http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports

# Only allow cachemgr access from localhost
http_access allow localhost manager
http_access deny manager

# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost

#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
acl hpcsalab src 10.10.10.0/24
acl centos7 src 10.10.10.129
acl cdac-time time A 18:00-20:00
acl cdac dstdomain .cdac.in
acl badwords url_regex -i "/etc/squid/badwords.txt"
acl blocked_sites dstdomain "/etc/squid/blocked-sites.txt"
acl centos7-blocked dstdomain "/etc/squid/centos7-blocked.txt"
http_access allow cdac-time
http_access deny centos7-blocked centos7
http_access deny blocked_sites hpcsalab
http_access deny badwords hpcsalab
http_access allow hpcsalab
# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
#http_access allow localnet
http_access allow localhost

# And finally deny all other access to this proxy
http_access deny all

# Squid normally listens to port 3128
http_port 3128

# Uncomment and adjust the following to add a disk cache directory.
cache_dir ufs /var/spool/squid 2048 16 256
visible_hostname proxy.panda.demo
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid

#
# Add any of your own refresh_pattern entries above these.
#
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320

[root@STM1 squid]# vim /etc/squid/badwords.txt
torrent
cricket
ipl
football
movies
bookmyshow

[root@STM1 squid]# systemctl restart squid

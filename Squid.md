# INSTALL AND CONFIG SQUID ON RHEL/ CENTOS

To Install Squid

`#ffffff` yum install squid -y

Now changes are to be made in "squid.conf" file

      we can find squid.conf in path below:
      
      cd /etc/lib/squid/squid.conf

      Make sufficient changes:
      
      1.   find the line given below and uncomment it. Mostly it can be found on line number 62
      
            cache_dir ufs /var/spool/squid 128 16 256

            Legends:
            128 = Cache Size
            16 = means 16 sub-directories will be created in /spool/squid
            256 = means 256 sub-directories will be created in upper 16 sub directories
      
      2.   To customize the name of machine to be seen on error page insert line below cache_dir line

            visible_hostname proxy.panda.demo
      
      3.   Now to create swap directories

            squid -z

The squid.conf file will look something like this;

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

#################################################################     

LETS SEE FEW WAYS TO USE SQUID

#################################################################

# To Block On Entire Network

            1. Create a file in squid folder or any folder just mention proper folder address    
                  and write the domains you want to block over the network

                >  vim /etc/squid/blocked_sites.txt

                  .microsoft.com
                  .esakal.com
                  .redhat.com

            2. Edit squid.conf (Add acls and http_access)

            
                  ACL = Access control list
                  Syntax = acl "name you want to give" src(source) Network_IP
              
                >  vim squid.conf
            
                  Add acls and http_access under this line which you want to include
                        - Enter your network ip here in place of "10.10.10.0/24"
            
                  #
                  # INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
                  #
                  acl hpcsalab src 10.10.10.0/24
                  acl blocked_sites dstdomain "/etc/squid/blocked-sites.txt"
                  http_access deny blocked_sites hpcsalab
                  http_access allow hpcsalab

            3. Restart squid service
            
               systemctl restart squid

               
################################################################################################################
# BLOCKED FOR PARTICULAR CLIENT
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
# FOR A TIME PERIOD OR DAY

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
# FOR ANY WORDS

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

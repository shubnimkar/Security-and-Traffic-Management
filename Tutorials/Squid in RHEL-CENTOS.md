# INSTALL AND CONFIG SQUID ON RHEL/ CENTOS

To implement this I've taken ```3 VM's```

VM's of Centos 7.9 : ```Two```  

VM's of Windows server 2016 : ```One```


Config will be ```one master``` and other ```two client nodes```


```Master``` : You should have two network adapter ```NAT``` and ```HOST-ONLY```


```You can view in network settings in machine created, here you can see two adapters```

![master](https://github.com/shubnimkar/Alpha-one/assets/46809421/eae29d83-a410-4fa5-80d3-02cba454b2b6)

```ENS 37```

![ens37-1](https://github.com/shubnimkar/Alpha-one/assets/46809421/cddb94e2-c0a8-4697-97c1-e11a5efb3bc2)

```ENS 33```

![ens33-1](https://github.com/shubnimkar/Alpha-one/assets/46809421/19c1d0c6-ec7d-41af-ab10-546c4c5f9ec0)

# CLIENT1

![Client1](https://github.com/shubnimkar/Alpha-one/assets/46809421/5355eae8-637c-4cc0-8d42-70143684cfee)

# CLIENT2 (WINDOWS SERVER)

![Win-conf](https://github.com/shubnimkar/Alpha-one/assets/46809421/925a1c88-2e8d-496c-9a9a-49d93214f662)

# PROXY SETTINGS (TO BE DONE ON ALL CLIENT'S BROWSER)

```ON CENTOS MACHINE```

![STM2 - VMware Workstation 24-06-2023 12_15_07 (1)](https://github.com/shubnimkar/Alpha-one/assets/46809421/de66ba7e-2f07-4adb-97b5-2f61ab9eaef0)


```ON WINDOWS MACHINE```

![winproxy](https://github.com/shubnimkar/Alpha-one/assets/46809421/809b0cef-ce0d-4688-a4b2-ba5fce213f2e)

```Commands to be followed on master:```

```To Install Squid```

      yum install squid -y

```Now changes are to be made in "squid.conf" file```

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

```The squid.conf file will look something like this;```

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

# ------------------------------------------------------------------------------
     
# Lets see few ways, how we can use SQUID

# ------------------------------------------------------------------------------


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

               
# ------------------------------------------------------------------------------

# BLOCKED FOR PARTICULAR CLIENT

            1. Create a file in squid folder or any folder just mention proper folder address    
                        and write the domains you want to block over the network
                        here i've created centos7-blocked.txt
                            >  vim /etc/squid/centos7-blocked.txt
            
                              .microsoft.com
                              .redhat.com
                              .facebook.com
            
            2. Edit squid.conf (Add acls and http_access)
                 
                  
                  #
                  # INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
                  #
                  acl hpcsalab src 10.10.10.0/24
                  acl blocked_sites dstdomain "/etc/squid/blocked-sites.txt"
                  http_access deny blocked_sites hpcsalab
                  http_access allow hpcsalab
                  
                  #http_access allow localnet
                  http_access allow localhost

            3. Restart squid service
            
               systemctl restart squid
               
# ------------------------------------------------------------------------------
       
# FOR A TIME PERIOD OR DAY

            1. We can block or can allow any websites for any time slots or days.
                  Time will be in 24 HR format

                  Days have specific alphabets assigned 

                  Monday : M
                  Tuesday : T
                  Wednesday : W
                  Thursday : H
                  Friday : F
                  Saturday : A
                  Sunday : S

                  so acl format will be: 
                                          acl <acl-name> dstdomain <any sitename>
                  this can be done to bunch of websites too as we have done above

                  Here I've taken bookmyshow.com for example to block on sturday between evening 6 PM - 8 PM

            2. Edit squid.conf (Add acls and http_access)

            
                  #
                  # INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
                  #
                  acl my-time time A 18:00-20:00
                  acl cdac dstdomain .bookmyshow.com
                  http_access deny my-time
                  
                  #http_access allow localnet
                  http_access allow localhost
            
            3. Restart squid service
            
               systemctl restart squid

               
# ------------------------------------------------------------------------------

# FOR ANY WORDS WE WANT TO BLOCK

            1. Make a file with all words you want to ban one by one in lines below in one file
               
                     > vim /etc/squid/badwords.txt
                            torrent
                            cricket
                            ipl
                            football
                            movies
                            bookmyshow

            
            2. Edit squid.conf (Add acls and http_access)
            
            #
            # INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
            #
            acl hpcsalab src 10.10.10.0/24
            acl badwords url_regex -i "/etc/squid/badwords.txt"
            http_access deny badwords hpcsalab
            http_access allow hpcsalab
            #http_access allow localnet
            http_access allow localhost
            
            3. Restart squid service
                  
                  systemctl restart squid

# ------------------------------------------------------------------------------

# Squid Authentication 

1. Add this in squid.conf file
   
   ```auth_param basic program /usr/lib64/squid/basic_ncsa_auth /etc/squid/squid-users```

   ```auth_param basic children 5```
            Children means number of users you want to create
     
   ```auth_param basic realm Squid Basic Authentication```
   
   ```auth_param basic credentialsttl 2 hours```
            Credentialssttl : facilitates admin to set password time for users


2. Edit squid.conf (Add acls and http_access)

Define ACL's : 

Syntax of ACL :   ```acl name of user proxy_auth name of user```

            
            #
            # INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
            #
            
            auth_param basic program /usr/lib64/squid/basic_ncsa_auth /etc/squid/squid-users
            auth_param basic children 5
            auth_param basic realm Squid Basic Authentication
            auth_param basic credentialsttl 2 hours
            acl acts_users proxy_auth REQUIRED
            
            acl user1 proxy_auth user1
            acl user1-access dstdomain "/etc/squid/user1.txt"
            acl all_web dstdomain .
            
            acl panda proxy_auth panda
            acl panda-access dstdomain "/etc/squid/panda.txt"
            
            http_access allow !user1-access user1
            http_access allow !panda-access panda
            
            http_access allow all_web acts_users
            http_access allow localhost
            
            # And finally deny all other access to this proxy
            http_access deny all

3. Restart squid service
                              
      systemctl restart squid

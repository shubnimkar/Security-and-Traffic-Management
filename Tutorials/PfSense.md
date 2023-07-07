<details><summary>Prerequisites</summary>


        Here I've three VM's

        1. New VM where will we install PFsense
        2. Centos 7.9 
        3. Windows server 

Download pfsense ISO from link below
    
    https://www.pfsense.org/download/

![pfse](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/30c14ef5-72bd-47aa-abac-88faeca5ce14)

</details>


 And we are good to go....!!!

# ------------------------------------------------------------------------------

# Create VM with following specifications:

        1. Machine config should be Debian 10x.64bit 
        
        2. There should be 2 network adapters
            1. NAT
            2. Host-only
        
        3. Disk space > 50GB's
        
        4. RAM as per the user's config

        5. Processors as per user's config
        
![Capture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/9e16065a-401d-48c6-822f-d555ee3a1ff5)

# ------------------------------------------------------------------------------

# Now power on the VM with pfsense image

                You'll see something like this on screen
                
                It'll automatically start the next sequence

![Capture PNG1](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/8f5bdf04-990c-4718-afd0-e614b1be26cd)

# ------------------------------------------------------------------------------

                Accept the Notice and proceed
                
![Captu1re](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/147f0bae-6988-44af-b18b-483cf5b9faaa)

# ------------------------------------------------------------------------------

                Select Install pfsense
                
![Cap1ture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/411605e6-fbc9-4cb8-85f2-15c6cb808470)

# ------------------------------------------------------------------------------

                Continue with default keymap
                
![C1apture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/06da48eb-ddf1-42ba-a600-8820f2b556fc)

# ------------------------------------------------------------------------------

                Auto ZFS

![Cap11ture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/635701a1-8296-46db-aee1-85a7cea78b30)

# ------------------------------------------------------------------------------

                Install >> Proceed with installation
                
![Capture1](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/53db21d9-e4a9-4848-977f-521e4c642dcf)

# ------------------------------------------------------------------------------

                Stripe - No redundancy
                
![Cap222ture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/e70e7209-6abb-4b03-bbf7-43120ab2d0f7)

# ------------------------------------------------------------------------------

                ZFS Configuration
                
                Press Space to select and proceed
                
![spacedabana](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/96c87aae-9d24-4ad5-83c0-d4a40a919ee2)

# ------------------------------------------------------------------------------

                Select for partition
                
                go for yes 
                
![2Capture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/41df2382-624d-4607-beb0-5cb7987aadb2)

# ------------------------------------------------------------------------------

                Installation will now begin..
                
![Ca234pture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/e75bc769-9179-429e-a7f3-8a54a49c3fcc)

# ------------------------------------------------------------------------------

                Select No
                
![Captu234re](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/27c298f6-6bcc-4e67-a107-b4e803e68b39)

# ------------------------------------------------------------------------------

                Reboot
                
![reebootCapture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/b5f65af5-4024-40da-be00-4e249173fb02)

# ------------------------------------------------------------------------------

# Installation is completed and this is the main menu for pfsense

![after](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/8f3d96b2-50d6-42c7-bb6f-773edaeb9b33)

# ------------------------------------------------------------------------------

# Now to set interfaces IP Address 

                Select 2 from options
                
                Then will ask for number of instances
                I've Configured 2 instances
                
                FOR LAN
                
                Enter the IP address of desire but of " host-only " network
                Here i've taken : 10.10.10.140
                Then subnet
                Subnet : 24


![1](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/50ad9e63-c526-4708-8e24-cc781e1f2b29)

                FOR WAN
                
                Just press enter and mark options as no 
                finally press enter for confirmation

![wan](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/70d7be16-01e2-4ec4-9fbf-f1090fe60b0a)

# ------------------------------------------------------------------------------

# Configure your client machines:

                Here, lets do it for one of our client 
                I'm doing it on one which is having centos 7 installed
                
                On terminal run "nmtui"
                
                now select your network adapter here is "ens33"
                
                Select IPv4 CONFIGURATION <MANUAL>
                Address : 10.10.10.142 (Should be in range of our host-only network )
                Gateway : 10.10.10.140 (Our configured pfsense address)
                DNS servers : 10.10.10.140 (Our configured pfsense address)

![nmtui](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/828eac63-bd06-4c36-a1a1-e98b75214372)

# ------------------------------------------------------------------------------

# Check IP on client machine 

                On terminal run "ip a"
                and check if your machine is getting our ip 10.10.10.142
                
![ip client](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/05f827e8-20c8-4325-a392-6dbcbae96c8d)

# ------------------------------------------------------------------------------

# Check if your nameserver are configured eitherwise you will not be able to connect to network

![checking ip a](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/7447a799-38eb-46ae-806f-0d0ea60f2b6d)

# ------------------------------------------------------------------------------

# If not then you can add in resolv.conf

                add entry in resolv.conf file
                
                vim /etc/resolv.conf
                
                nameserver 192.168.100.2 (This is IP in your pfsense machine NAT network address just replace last octet ip number with 2)

![network nahi chala to](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/9595f34a-c9cd-4114-8d23-9fdea917dfe2)

# ------------------------------------------------------------------------------

# TILL HERE WE'VE SEEN PFSENSE INSTALLATION AND CLIENT CONFIGURATION 

TO SUMMARIZE TILL NOW :

Pfsense IS OUR FIREWALL WHICH HAS 2 NETWORKS : NAT ,HOST-ONLY

CLIENTS WILL ALWAYS BE IN HOST-ONLY 

AND CLIENT MACHINES WILL BE ABLE TO ACCESS NETWORK THROUGH OUR FIREWALL

# ------------------------------------------------------------------------------

# Let's see Pfsense config. on web UI

                we've given host-only IP as 10.10.10.140
                
                Open your browser and paste the same ip and get going

                The login page 
                
                Use credentials below to login
                
                Default Username : admin
                Default Password : pfsense

![login](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/a802d56c-78fd-4a5d-9229-c54bfca30f11)

# ------------------------------------------------------------------------------

# Let's configure :

                Landing page 
                
                
![setup](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/026513ac-2b45-4449-b2f4-09e506a54a74)

                Click next


![Capture2](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/cbf22cd0-1249-43d6-b17d-7fcb090dd2b5)

                Click next

                Enter Primary DNS Server : 192.168.100.2 (NAT address DNS)


![s2](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/d0c1c987-33d5-476c-ba48-5703be00ae7f)

                Select Time Zone

![pfSense - Login - Google Chrome 26-06-2023 17_25_47](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/94761e35-df1c-42d4-89f3-9bd243df82bd)


                I'm setting this for DHCP hence selecting DHCP and made no change in entire page and next

![41](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/d86dc827-4e94-4544-bfa4-d445c3e5d4f6)
![43](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/0e50d5ab-e461-4409-97b6-33bc8de6b523)
![44](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/bcfc132b-0c8a-4952-abf2-4a0cc0b96059)


                NO need to make changed as we've already done in CLI 

![pfSense home arpa - Wizard_ pfSense Setup_ Configure LAN Interface - Google Chrome 26-06-2023 17_28_03](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/84f38e7c-cd19-4cc8-88ff-ef3c01b6a322)


                Setup Your password (It'll change your default password for portal)

![pfSense home arpa - Wizard_ pfSense Setup_ Configure LAN Interface - Google Chrome 26-06-2023 17_28_20](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/210aa9f4-c5ec-40d6-a1e5-cabb64086e45)


                Reload

![pfSense home arpa - Wizard_ pfSense Setup_ Configure LAN Interface - Google Chrome 26-06-2023 17_28_26](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/977b462e-b174-4fe9-a108-bf1b7824bffe)


![pfSense home arpa - Wizard_ pfSense Setup_ Configure LAN Interface - Google Chrome 26-06-2023 17_28_31](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/73d34e8e-662d-4daa-8a42-7a52d60a5ba8)

                Pfsense configuration is complete

![pfSense home arpa - Wizard_ pfSense Setup_ Configure LAN Interface - Google Chrome 26-06-2023 17_28_36](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/9b085245-2159-4ee4-915e-4ab23937046f)

# ------------------------------------------------------------------------------

# This is Main Dashboard

![pfSense home arpa - Wizard_ pfSense Setup_ Configure LAN Interface - Google Chrome 26-06-2023 17_32_06](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/7f7e8127-5a11-4239-9e45-7a7245e1b959)

# ------------------------------------------------------------------------------

# Let's do trial if our firewall is working or not

                I want to block a single website
                
                here that is www.hotstar.com 
                
                Find IP of hotstar for the same , because this firewall only works with IP not with domain names
                

![fr](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/b4897398-1d92-49a4-8dbe-9e3ddd5f9e50)

                Go to Firewall >> Rules >> LAN >> Add (UP arrow add)

                
![pfSense home arpa - Wizard_ pfSense Setup_ Configure LAN Interface - Google Chrome 26-06-2023 17_43_13](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/f3239247-4323-491b-9e4f-2d9a646ea180)

                
                        Choose Action : Block
                        Interface : LAN
                        
                        Destination:
                                Single host or alias 108.159.80.89 (IP of hotstar)
                                Destination Port Range : HTTP 443
                        
                        >> Save


                Click on apply changes

![pfSense home arpa - Wizard_ pfSense Setup_ Configure LAN Interface - Google Chrome 26-06-2023 17_43_24](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/f2006dd6-1a5b-48e2-af4d-1415efe42ddc)

![pfSense home arpa - Wizard_ pfSense Setup_ Configure LAN Interface - Google Chrome 26-06-2023 17_43_48](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/63c23315-84ae-4ce9-9118-6c10661840aa)


# Now go to client machine and open your browser and try to access for websites. 

                Here we are able to access wikipedia.org and reddit.com 

![w](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/9a962f4e-7049-47c1-b65b-eb7d857ba3dc)

![r](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/80ec1fa5-ec9a-4561-8fca-a7d471ce2729)

                and now go for www.hotstar.com 
                
![h](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/8c4a0552-657d-4900-84d6-6bc7393d9207)

                so we are able to access other website and not the hotstar.com , so it verifies our task

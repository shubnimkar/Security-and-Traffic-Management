# Prerequisites


        Here I've three VM's

        1. New VM where will we install PFsense
        2. Centos 7.9 
        3. Windows server 

Download pfsense ISO from link below
    
    https://www.pfsense.org/download/

![pfse](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/30c14ef5-72bd-47aa-abac-88faeca5ce14)

And we are good to go....!!!

# Create VM with following specifications:

        1. Machine config should be Debian 10x.64bit 
        
        2. There should be 2 network adapters
            1. NAT
            2. Host-only
        
        3. Disk space > 50GB's
        
        4. RAM as per the user's config

        5. Processors as per user's config
        
![Capture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/9e16065a-401d-48c6-822f-d555ee3a1ff5)

# Now power on the VM with pfsense image
You'll see something like this on screen
It'll automatically start the next sequence
![Capture PNG1](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/8f5bdf04-990c-4718-afd0-e614b1be26cd)

Accept the Notice and proceed
![Captu1re](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/147f0bae-6988-44af-b18b-483cf5b9faaa)

Select Install pfsense
![Cap1ture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/411605e6-fbc9-4cb8-85f2-15c6cb808470)

Continue with default keymap
![C1apture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/06da48eb-ddf1-42ba-a600-8820f2b556fc)

Auto ZFS
![Cap11ture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/635701a1-8296-46db-aee1-85a7cea78b30)

Install >> Proceed with installation
![Capture1](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/53db21d9-e4a9-4848-977f-521e4c642dcf)

Stripe - No redundancy
![Cap222ture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/e70e7209-6abb-4b03-bbf7-43120ab2d0f7)

ZFS Configuration
Press Space to select and proceed
![spacedabana](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/96c87aae-9d24-4ad5-83c0-d4a40a919ee2)

Select for partition
go for yes 
![2Capture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/41df2382-624d-4607-beb0-5cb7987aadb2)

Installtion will now begin..
![Ca234pture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/e75bc769-9179-429e-a7f3-8a54a49c3fcc)

Select No 
![Captu234re](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/27c298f6-6bcc-4e67-a107-b4e803e68b39)

Reboot
![reebootCapture](https://github.com/shubnimkar/Security-and-Traffic-Management/assets/46809421/b5f65af5-4024-40da-be00-4e249173fb02)


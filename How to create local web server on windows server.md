Here we will understand how to create a local server on windows server and host a locally created static webpage.

We just need a machine installed with any Windows Server OS.


## Open server manager to create a server:

* #### Step 1
  * Local Server 
  * Add roles and features
    
![Windows Server 2016 (1) - VMware Workstation 30-06-2023 19_37_57](https://github.com/shubnimkar/Alpha-one/assets/46809421/63c4cdc1-975c-442c-9bbb-9a63cebd2798)

* #### Step 2
  * Next
    
![Windows Server 2016 (1) - VMware Workstation 30-06-2023 19_38_11](https://github.com/shubnimkar/Alpha-one/assets/46809421/8e74889e-7995-4e71-aa1e-94184ccf057f)

* #### Step 3
  * Role based or feature based installation
  * Next

![Windows Server 2016 (1) - VMware Workstation 30-06-2023 19_38_16](https://github.com/shubnimkar/Alpha-one/assets/46809421/57b404ed-4f26-4d03-b6a1-eb079375e4d7)

* #### Step 4
  * Select from server pool
  * Next
    
![Windows Server 2016 (1) - VMware Workstation 30-06-2023 19_38_22](https://github.com/shubnimkar/Alpha-one/assets/46809421/119d8c53-49ef-4122-b73c-d87cb1d81c6b)

* #### Step 5
  * Select Web Server IIS from list
  * Next
    
![Windows Server 2016 (1) - VMware Workstation 30-06-2023 19_38_40](https://github.com/shubnimkar/Alpha-one/assets/46809421/778d90e8-1b60-43c7-a8eb-b89c9dda77c1)

* #### Step 6
  * Next
    
![Windows Server 2016 (1) - VMware Workstation 30-06-2023 19_38_50](https://github.com/shubnimkar/Alpha-one/assets/46809421/fa92c619-3fe0-4dc0-a01e-9cad82f770bd)

* #### Step 7
  * Install
    
![Windows Server 2016 (1) - VMware Workstation 30-06-2023 19_39_37](https://github.com/shubnimkar/Alpha-one/assets/46809421/8e2eef3f-bfd3-48b3-b57e-1581b309d1e2)

### Finally on server manager you can see the created server

![Windows Server 2016 (1) - VMware Workstation 30-06-2023 19_37_43](https://github.com/shubnimkar/Alpha-one/assets/46809421/749f3ce9-05c0-42bf-89a8-9f116338daf3)



## Now let's create a static web page to see in our webserver is working or not

* #### Step 1
  * Go to C-drive
  * Search for *inetpub* folder
  * Create folder for your website
  
![Windows Server 2016 (1) - VMware Workstation 01-07-2023 15_55_40](https://github.com/shubnimkar/Alpha-one/assets/46809421/2a9c78d5-0ab2-460f-94de-29e3d88f5e6a)

* #### Step 2
   * Create one html page inside the folder but be aware to name html file *index.html* only other wise it will not bind to IP
     
![Windows Server 2016 (1) - VMware Workstation 01-07-2023 15_56_27](https://github.com/shubnimkar/Alpha-one/assets/46809421/2650956d-cc6c-4663-9856-d2e22979b56d)

* #### Step 3
 * Now go to IIS from your server manager > click on your local server > Manage > IIS
 * This page will open
 * Right click on sites and add website
 * Enter the site name as per your need
 * select the path for the page we created in our local machine
 * add IP or port , here I want to host it on port 7000
   
![Windows Server 2016 (1) - VMware Workstation 01-07-2023 15_59_31](https://github.com/shubnimkar/Alpha-one/assets/46809421/bcde73a8-b9b6-4219-9497-b300b6a32c53)

* #### after adding the site it'll look something like this,
  
![Windows Server 2016 (1) - VMware Workstation 01-07-2023 15_59_38](https://github.com/shubnimkar/Alpha-one/assets/46809421/29025474-374d-4eda-bc2a-ec9c2915ec1f)

* #### Now got to browser put your local ip of machine and port number and VOILA..!!


![Windows Server 2016 (1) - VMware Workstation 01-07-2023 16_00_24](https://github.com/shubnimkar/Alpha-one/assets/46809421/4476a881-d3ba-4bca-a4b4-77683bbe1e89)

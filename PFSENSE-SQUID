
services > squid proxy > local cache >Squid Hard Disk Cache Settings > Hard Disk Cache Size >2048

![pfSense home arpa - Package_ Proxy Server_ Cache Management_ Local Cache - Google Chrome 27-06-2023 18_24_59](https://github.com/shubnimkar/Alpha-one/assets/46809421/75017c98-c944-4913-ad78-9b5b7ef190d7)
![pfSense home arpa - Package_ Proxy Server_ Cache Management_ Local Cache - Google Chrome 27-06-2023 18_26_40](https://github.com/shubnimkar/Alpha-one/assets/46809421/71f28df8-b735-449d-964d-600b8b8d28a9)

Squid General Settings >Enable Squid Proxy > Check
Proxy Interface(s) > select LAN and loopback (select using control)
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_29_28](https://github.com/shubnimkar/Alpha-one/assets/46809421/fc147b93-e761-4637-bbb7-e303938e3f63)


Logging Settings > Enable Access Logging > check tick
![Capture](https://github.com/shubnimkar/Alpha-one/assets/46809421/16a19f31-3bb4-4947-848e-7d23e06a1015)

Headers Handling, Language and Other Customizations >Visible Hostname>Administrator's Email> save
![sa](https://github.com/shubnimkar/Alpha-one/assets/46809421/453832ea-cd35-4096-9dc0-4d2b5d583b99)

go to client and proxy IP pf browser
![1](https://github.com/shubnimkar/Alpha-one/assets/46809421/fdd84f15-12f4-4e31-847e-f7e30c1e9b9e)

check in browser and find if sites are working if working then fine 


for blocking
ACL's > Squid Access Control Lists > Allowed Subnets > 10.10.10.0/24

![211](https://github.com/shubnimkar/Alpha-one/assets/46809421/c6715a4b-3a29-4a99-885e-555f16f05cfe)
![222](https://github.com/shubnimkar/Alpha-one/assets/46809421/54e096d7-6197-45c1-ae3d-0b6645eeac8a)
![212](https://github.com/shubnimkar/Alpha-one/assets/46809421/4ab6de66-1c03-49b8-b2d9-98e741878f8c)
 go to general and restart


# Squid guard

https://dsi.ut-capitole.fr/blacklists/download/

copy link
pfsense tar

https://dsi.ut-capitole.fr/blacklists/download/blacklists_for_pfsense.tar.gz



to squidguard 
general page and go to last and click blacklist
paste url save 
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_55_53](https://github.com/shubnimkar/Alpha-one/assets/46809421/5736d1d2-c842-4146-b4de-3e98c32a6805)
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_56_02](https://github.com/shubnimkar/Alpha-one/assets/46809421/519a3904-7b73-4d4f-9238-23c89bae2897)


goto blacklist download
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_55_38](https://github.com/shubnimkar/Alpha-one/assets/46809421/dbd30985-e343-4f76-bdc5-9cb433e5eadd)
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_55_46](https://github.com/shubnimkar/Alpha-one/assets/46809421/e7b3849e-4214-4e3d-8ad3-686d3a0e5ebe)


Go to target cat (we have to cretae 2)
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_58_15](https://github.com/shubnimkar/Alpha-one/assets/46809421/045e79df-7686-483e-a8e1-9a4052e9c6ae)
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_59_04](https://github.com/shubnimkar/Alpha-one/assets/46809421/911ccd78-ebb4-4d72-b3da-51686fc2bff6)
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_59_13](https://github.com/shubnimkar/Alpha-one/assets/46809421/3ddd8c09-7e70-4baf-a6b9-86d9ead40f80)
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_59_31](https://github.com/shubnimkar/Alpha-one/assets/46809421/b94dea1a-f233-4af6-9eef-d94ca3849ccd)
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_59_41](https://github.com/shubnimkar/Alpha-one/assets/46809421/92fdaa8c-40d0-4281-b06a-5e21872d37df)
![pfSense home arpa - Package_ Proxy Server_ General Settings_ General - Google Chrome 27-06-2023 18_59_46](https://github.com/shubnimkar/Alpha-one/assets/46809421/408bbc16-4c47-413f-a06c-e2276562ff15)

general page 
enable tick 
enable log 
save


![pfSense home arpa - Package_ Proxy filter SquidGuard_ General settings_ General settings - Google Chrome 27-06-2023 19_04_26](https://github.com/shubnimkar/Alpha-one/assets/46809421/af4ae0f9-518c-4177-9198-d4265f215922)
![pfSense home arpa - Package_ Proxy filter SquidGuard_ General settings_ General settings - Google Chrome 27-06-2023 19_04_32](https://github.com/shubnimkar/Alpha-one/assets/46809421/d3317744-1b05-4a76-af6a-0a7963f8b2b4)


COMMON ACL
+ target list

![Editing Alpha-one_pfsense-squid md at master · shubnimkar_Alpha-one · GitHub - Google Chrome 27-06-2023 19_05_57](https://github.com/shubnimkar/Alpha-one/assets/46809421/83c6210f-b3b6-4444-a9d9-80657630110b)
![Editing Alpha-one_pfsense-squid md at master · shubnimkar_Alpha-one · GitHub - Google Chrome 27-06-2023 19_06_47](https://github.com/shubnimkar/Alpha-one/assets/46809421/5ca3b230-76f3-409f-b46b-18ca3d0464d3)
![Editing Alpha-one_pfsense-squid md at master · shubnimkar_Alpha-one · GitHub - Google Chrome 27-06-2023 19_06_58](https://github.com/shubnimkar/Alpha-one/assets/46809421/f44134e7-be54-48cf-9488-318e5258415e)
![pfSense home arpa - Package_ Proxy filter SquidGuard_ Common Access Control List (ACL)_ Common ACL - Google Chrome 27-06-2023 19_07_22](https://github.com/shubnimkar/Alpha-one/assets/46809421/a3d0acb2-e453-4154-a346-19196c427d27)
![pfSense home arpa - Package_ Proxy filter SquidGuard_ Common Access Control List (ACL)_ Common ACL - Google Chrome 27-06-2023 19_07_42](https://github.com/shubnimkar/Alpha-one/assets/46809421/e6ecf614-a3b4-4970-bed9-6eb5ffa5047d)

apply

![pfSense home arpa - Package_ Proxy filter SquidGuard_ General settings_ General settings - Google Chrome 27-06-2023 19_07_52](https://github.com/shubnimkar/Alpha-one/assets/46809421/6709dbe4-1496-4fa5-9554-87a921e799d7)

target cat > allowed
![pfSense home arpa - Package_ Proxy filter SquidGuard_ General settings_ General settings - Google Chrome 27-06-2023 19_16_03](https://github.com/shubnimkar/Alpha-one/assets/46809421/fe5a7db0-cb95-4110-98fc-8a17955d6cdd)
![pfSense home arpa - Package_ Proxy filter SquidGuard_ General settings_ General settings - Google Chrome 27-06-2023 19_16_12](https://github.com/shubnimkar/Alpha-one/assets/46809421/2e9bb2a2-6851-43a6-b6cd-dcdd39a8d479)

apply

Group ACL
![pfSense home arpa - Package_ Proxy filter SquidGuard_ General settings_ General settings - Google Chrome 27-06-2023 19_39_44](https://github.com/shubnimkar/Alpha-one/assets/46809421/9f7b5233-45a4-49df-a4ae-f6f27d9a1185)

ADD

cliemt source for client withpout time
![Editing Alpha-one_pfsense-squid md at master · shubnimkar_Alpha-one · GitHub - Google Chrome 27-06-2023 19_47_12](https://github.com/shubnimkar/Alpha-one/assets/46809421/c455142f-741b-4a67-a4f5-5a85cf713137)
![Editing Alpha-one_pfsense-squid md at master · shubnimkar_Alpha-one · GitHub - Google Chrome 27-06-2023 19_44_08](https://github.com/shubnimkar/Alpha-one/assets/46809421/283f00f9-23ef-4cf0-87df-a9a194baddc5)
![Editing Alpha-one_pfsense-squid md at master · shubnimkar_Alpha-one · GitHub - Google Chrome 27-06-2023 19_44_58](https://github.com/shubnimkar/Alpha-one/assets/46809421/fc7b3843-0909-481e-b368-f58e0f78b997)
![Editing Alpha-one_pfsense-squid md at master · shubnimkar_Alpha-one · GitHub - Google Chrome 27-06-2023 19_45_07](https://github.com/shubnimkar/Alpha-one/assets/46809421/da45ee9a-f4ce-43ce-b413-4ab28b309871)

Squid proxy 
users
![Alpha-one_pfsense-squid md at master · shubnimkar_Alpha-one · GitHub - Google Chrome 27-06-2023 20_07_24](https://github.com/shubnimkar/Alpha-one/assets/46809421/67d5bbf9-69cf-4feb-92cc-0e5f0b02b02d)
![Alpha-one_pfsense-squid md at master · shubnimkar_Alpha-one · GitHub - Google Chrome 27-06-2023 20_08_55](https://github.com/shubnimkar/Alpha-one/assets/46809421/ab9258d5-c43a-41f6-ad5b-f2324a22cd80)
![Alpha-one_pfsense-squid md at master · shubnimkar_Alpha-one · GitHub - Google Chrome 27-06-2023 20_09_00](https://github.com/shubnimkar/Alpha-one/assets/46809421/73000473-a312-4988-af4e-eafe843e799b)



![pfSense home arpa - Package_ Proxy Server_ Authentication_ Authentication - Google Chrome 27-06-2023 20_12_38](https://github.com/shubnimkar/Alpha-one/assets/46809421/594367a2-a411-4b66-b671-b3070d6bf834)
![pfSense home arpa - Package_ Proxy Server_ Authentication_ Authentication - Google Chrome 27-06-2023 20_10_14](https://github.com/shubnimkar/Alpha-one/assets/46809421/bbb5b84f-ebe6-48f9-80be-ba1989e62da8)


![pfSense home arpa - Package_ Proxy Server_ Authentication_ Authentication - Google Chrome 27-06-2023 20_12_06](https://github.com/shubnimkar/Alpha-one/assets/46809421/9d094bbc-b31d-4dcb-a906-ed692e15d4f8)
![pfSense home arpa - Proxy filter SquidGuard_ Groups Access Control List (ACL)_ Edit_ Groups ACL - Google Chrome 27-06-2023 20_13_20](https://github.com/shubnimkar/Alpha-one/assets/46809421/b1d323ca-be13-443a-8023-3b1676398fa0)

![pfSense home arpa - Proxy filter SquidGuard_ Groups Access Control List (ACL)_ Edit_ Groups ACL - Google Chrome 27-06-2023 20_26_14](https://github.com/shubnimkar/Alpha-one/assets/46809421/d67f7c36-8825-4b55-aad2-88b9df0e1873)
![pfSense home arpa - Proxy filter SquidGuard_ Target categories_ Edit_ Target categories - Google Chrome 27-06-2023 20_26_26](https://github.com/shubnimkar/Alpha-one/assets/46809421/8434839a-8d0b-45f4-9369-cd1ce2901d50)
![pfSense home arpa - Proxy filter SquidGuard_ Groups Access Control List (ACL)_ Edit_ Groups ACL - Google Chrome 27-06-2023 20_25_10](https://github.com/shubnimkar/Alpha-one/assets/46809421/6e68038f-cd0a-46db-91d0-9ba09c32a9c3)

got o group access + deny bad words
genral restart

### Network 1 : Lab #3
### By Ahmed Arafat (Ahmed Mohamed Yousry)

- First you have to statically `configure` the IP Address of the two PCs you have

- Then click on the switch and enter `CLI`
- Enter Privilege Mode
````
en
````

- Then Enter Configuration Level
````
conf t
````

- To name current Switch with name `vlan1`
````
int vlan1
````
> `int` stands for interface


- To give the switch an `IP Address`
````
ip add 192.168.1.2 255.255.255.0
````

- To turn it on
````
no sh
````
> `sh` stand for shutdown


- To show mac address table (at USER MOD level)
````
show mac-address-table
````

- Then inside any PC, enter command prompt then type
````
ping IPAddressOfOtherPC
````
> Example: `ping 192.168.1.3`


- When we were configuring our switch, we were connecting to it using the console port
- What if we want to connect to it remotely using virtual terminal like telnet


- First we enable a password (at switch config)
````
enable password arafat
````

- Then we will encrypt the password
````
service password-encryption
````

- Then enable secret (extra layer of security & protection)
````
enable secret class
````

- To print a message if login failed
````
banner motd "Hello Arafat"
````
> `motd` stands for `Message Of The Day`


- Now I want to till the switch that when I connect to it using the console port, then I have to enter that password
````
line con 0
password arafat
login
exit
````
> `con` stand for console port <br>
> `0` means the first port

- Now if I want to connect to our switch remotely then I have to enter our password
````
line vty 0 4
password arafat
login
exit
````
> `vty` is The virtual terminal or “VTY” lines are virtual lines that allow connecting to the device using telnet or Secure Shell (SSH) <br>
> `0 4`: means that the switch scan allow 5 simultaneous virtual connections which may be Telnet or SSH


- Inside `CMD` of amy PC type the following command to remotely connect to our switch
````
telnet IPAddressOfSwitch
````

- Then enter 
````
en
````
> Here you will have to enter the secret password (cic in our case)
    
- Inside that PC & in CONFIG MODE, type the following to change name of our switch
````
hostname SW1_CIC_Zayed_Room_A004
````

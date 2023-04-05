
- for static routing 
````
ip route 192.168.2.0 255.255.255.0 192.168.4.2
````
> Or you can configure it in router's menu `Config` > `Routing` > `Static` <br>
> Then add `Network` (192.168.2.0) /Mask(255.255.255.0) / Next Hop(192.168.4.2) Respectively





- There are two ways to add `DHCP` in your network, first by configuring 
the router itself so that it will be responsible for assigning the IP Address
& the other way is by adding a server that contains the service `DHCP`



<img src="">

- Don't forget to add ip address of both ports (`192.168.1.1` & `192.168.1.2`)
````
en
conf t
````

````
int fa0/1
````

````
ip add 192.168.1.1 255.255.255.0
````

````
no sh
````

- In the router `CLI` add the name of the pool for LAN `1.0`
````
ip dhcp pool Router1
````

- Then add the Network Address for that LAN (each host will have the same Network Address [`Same first Three octet`])
````
network 192.168.1.0 255.255.255.0
````

- then type the default gateway 
````
default-router 192.168.1.1
````

- Then type following command if you want to exclude some IP Addresses (optional step)
````
ip dhcp excluded-address 192.168.1.1 192.168.1.5 
````
> Note: You may want to exclude some IP Addresses as you will assign these IP Addresses to your servers (IP Address of a server will most likely be assigned statically)








- `DHCP` means Dynamic Host Configuration Protocol

- add a server
- then give it `IP Address` (192.168.1.3)/ subnet mask (255.255.255.0) / default gateway (192.168.1.1)
from desktop > IP Configuration

- Then inside `services` tab go to `DHCP`
- turn service to `on`
- add pool name (any name you want)
- default gateway ( the IP Address of the router that is connected to that LAN like `192.168.1.1` )
- Then in Start IP Address choose the start IP you want (if you typed `192.168.1.10` means you have excluded from `192.168.1.1` to `192.168.1.9`) 
- Then add subnet mask : `255.255.255.0`
- Then choose maximum of users


- Same steps will be applied to LAN `2.0` & `3.0`


- Now to make Router #1 for LAN `1.0` knows the IP address of DHCP Server,
,enter the router then in `CLI` enter the interface (port) 
with IP Address `192.168.1.1`
````
int fa0/0
````
- Then type the following command
````
ip helper-address IP_Address_Of_DHCP_Server
````
> Note: if you added the `DHCP Server` in Lan `3.0` then,
then the above commands will not be written for that LAN,
it will be written in the two routers of LANs `1.0` & `2.0`

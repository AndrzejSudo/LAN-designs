Network LAN topologies
==================

Several simulated network designs made in GNS3 VMware and Packet Tracer, utilizing Cisco devices and services.
All of them are aligned with Cisco Certified Network Associate level, as I was creating them as part of my journey towards CCNA certification.

------------

Available networks:

- Campus 	- 3-tier design, with routers as core layer, multilayer switches as distribution and switches as access layer. 4 configured VLANs with centralized DHCP server for PC endpoints. Inter-vlan routing done via SVIs on L3 switches, which are also set-up as DHCP relay agents. Configured ROAS sub-interfaces on routers and DHCP server for IP addresses assignment to specific subnets. Static routes and floating static routes for default gateway were also configured between routers and L3 switches. L3 switches can't access Internet. All PC clients can reach eachother.
![design](campus/Design.JPG?raw=true "Campus LAN")

----------------

- Office 	- 2-tier design, with routers as distribution layer and switches as access. Network divided into multiple VLANs, some for correct number of endpoints and some with spare hosts in subnet for scalability. 802.1Q Trunk links on switches and ROAS sub-interfaces on routers have been configured to allow communication between VLANs. OSPF dynamic routing protocol configured on routers to learn routes to each VLAN. ACLs have been configured on routers, following rules: only VLAN21/22 hosts can SSH to CR routers, endpoint can only ping loopback interfaces of CR routers from their local networks, only host in local subnets can access printers, hosts in VLAN 30 can't access servers. All PC clients can ping eachother.
![design](office/Design.JPG?raw=true "Campus LAN") 

----------------

- Data center 	- spine-leaf multi-tier design with additional fault tolerant redundant links. CR routers as core layer, SSW L3 switches as service layer, DSW L3 switches as distribution layer, ASW switches as access layer. L2 LACP etherchannels configured between multilayer switches. First hop redundancy protocol HSRP with virtual default gateway for servers, configured on SVI of DSW1 and DSW2 switches. DSW1 configured to be root bridge. Portfast, BPDU guard, port security enabled on ASW interfaces connected to clients. NAT Overload/PAT configured on CR routers outside interfaces, towards provider edge router. SSW switches are configured in NTP symetric active mode and act as NTP servers in network. Servers can reach PE network.
![design](dataCenter/Design.jpg?raw=true "Campus LAN") 

----------------

- Small Office/Home Office - star-hybrid topology utilizing Lightweight Wireless Access Points, managed by Wireless LAN Controller, via CAPWAP tunnel. LWAPs operate in FlexConnect mode, without sending data traffic through WLC. LWAPs form ESS network and share same SSID for redundancy - if one of the APs fails, its clients will automatically connect to other AP. WLC and LWAPs are part of management VLAN 10 and wireless clients are placed in VLAN 100. WLC provides IP addresses for devices in VLAN 10 and router R1 is DHCP server for clients in VLAN 100. Trunk links on switch and ROAS sub-interfaces on router have been configured to allow communication between VLANs.
![design](SOHO/Design.jpg?raw=true "SOHO network") 


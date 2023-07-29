Network LAN topologies
==================

Several simulated network designs made in GNS3 VMware and Packet Tracer, utilizing Cisco devices and services.
All of them are aligned with Cisco Certified Network Associate level, as I was creating them as part of my journey towards CCNA certification.

------------

Available networks:

- Campus 	- 3-tier design, with routers as core layer, multilayer switches as distribution and switches as access layer. 4 configured VLANs with centralized DHCP server for PC endpoints. Inter-vlan routing done via SVIs on L3 switches, which are also set-up as DHCP relay agents. Configured ROAS sub-interfaces on routers and DHCP for IP addresses assignment to specific subnets. Floating static routes for default gateway were also configured between routers and Internet PE router. L3 switches can't access Internet. All hosts can ping eachother. 

- Office 	- 2-tier design, with routers as distribution layer and switches as access. Network divided into multiple VLANs, some for correct number of endpoints and some with spare hosts in subnet for scalability. Trunk links on switches and ROAS sub-interfaces on routers have been configured to allow communication between VLANs. OSPF dynamic routing protocol configured on routers to learn routes to each VLAN. ACLs have been configured on routers, following rules: only VLAN21/22 hosts can SSH to CR routers, endpoint can only ping loopback interfaces of CR routers from their local networks, only host in local subnets can access printers, hosts in VLAN 30 can't access servers.

- Data center 	-

----------------





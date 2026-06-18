# [CCNP-Auto Link](https://github.com/kuterek21/Python_for_Cisco/blob/main/README.md)
# CCIE-AUTO

 - [Routers Config](https://github.com/kuterek21/CCIE-AUTO/blob/main/Routers%20Prep)
 - to check if NETCONF is enabled:
     - ssh admin@10.255.0.1 -p 830 //  we shoud see list of #yang data models
  
## Tools:
### [Yang Suite](https://github.com/kuterek21/CCIE-AUTO/blob/main/YANG%20SUITE)
  

| Router_1 | Router_2 |
|----------|----------|
| ```bash
# Router_1
conf t
hostname IOSXE_1

int gi1
descript MGMT
ip add 10.255.1.1 255.255.255.0
no sh

int gi2
descri connected to IOSXE-2
ip add 12.0.0.1 255.255.255.0
no sh

int gi3
descri connected to IOS-3
ip add 13.0.0.1 255.255.255.0
no sh

int gi4
descri connected to IOS-4
ip add 14.0.0.1 255.255.255.0
no sh

!
router ospf 1
router-id 1.1.1.1

int range gi1/2
ip ospf 1 area 0

!
username mariusz priv 15 password cisco
ip domain-name abc.com
crypto key gen rsa modo 1024
ip ssh ver 2

line vty 0 4
login local
trans in all

!
! enable netconf
netconf ssh
netconf-yang

end
wr
!
``` | ```bash
# Router_2
conf t
hostname IOSXE_2

int gi1
descript MGMT
ip add 10.255.1.2 255.255.255.0
no sh

int gi2
descri connected to IOSXE-1
ip add 12.0.0.2 255.255.255.0
no sh

int gi3
descri connected to IOS-3
ip add 23.0.0.2 255.255.255.0
no sh

int gi4
descri connected to IOS-4
ip add 24.0.0.2 255.255.255.0
no sh

!
router ospf 1
router-id 2.2.2.2

int range gi1/2
ip ospf 1 area 0

!
! enable ssh
username mariusz priv 15 password cisco
ip domain-name abc.com
crypto key gen rsa modo 1024
ip ssh ver 2

line vty 0 4
login local
trans in all

!
! enable netconf
netconf ssh
netconf-yang

end
wr
!
``` |

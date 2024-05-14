en
conf t
iox
!
interface VirtualPortgroup 0
ip address 192.168.35.1 255.255.255.0
ip nat inside
no mop enabled
no mop sysid
exit
!
int gi 2
ip nat outside
exit
!
ip nat inside source list NAT_ACL interface GigabitEthernet 2 overload
ip access-list standard NAT_ACL
permit 192.168.35.0 0.0.0.255

!


app-hosting appid guestshell
app-vnic gateway1 virtualportgroup 0 guest-interface 0
guest-ipaddress 192.168.35.2 netmask 255.255.255.0
exit
app-default-gateway 192.168.35.1 guest-interface 0
name-server0 8.8.8.8
name-server1 10.10.10.25
end
!
guestshell enable

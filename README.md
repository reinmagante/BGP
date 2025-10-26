# BGP

NOC L1/T1/Service: Utusan ng bayan
http://msp.chevron.com/otrs/customer.pl
user1
C1sc0123


NOC T3/L3o r L4
http://msp.chevron.com/otrs/index.pl
root@localhost
C1sc0123



conf t
router eirgp 90
network 192.168.10.96 0.0.0.31
network 192.168.10.48 0.0.0.15

@r1
conf t
router bgp 1
bpg log neighbor-changes
neighbor 208.8.8.4 remote-as 45
neighbor 207.7.7.2 remote-as 2
neighbor 209.9.9.3 remote-as 3
network 208.8.8.0 mask 255.255.255.0
network 207.7.7.0 mask 255.255.255.0
network 209.9.9.0 mask 255.255.255.0
network 10.1.1.0 mask 255.255.255.252




@I1 

conf t
router bgp 45
bgp log-neighbor-changes
neighbor 45.4.5.5 remote-as 45
neighbor 24.2.4.2 remote-as 2
neighbor 208.8.8.1 remote-as 1
network 45.4.5.0 mask 255.255.255.0
network 24.2.4.0 mask 255.255.255.0
network 208.8.8.0 mask 255.255.255.0

!PretentInternet
network 0.0.0.0
ip route 0.0.0.0 0.0.0.0 null 0
ip route 10.0.0.0 255.0.0.0 208.8.8.1

@I2
conf t
no router bgp 45
router bgp 2
bgp log-neighbor-changes
neighbor 25.2.5.5 remote-as 45
neighbor 32.3.2.3 remote-as 3
neighbor 24.2.4.4 remote-as 45
neighbor 207.7.7.1 remote-as 1
network 25.2.5.0 mask 255.255.255.0
network 32.3.2.0 mask 255.255.255.0
network 24.2.4.0 mask 255.255.255.0
network  207.7.7.0 mask 255.255.255.0

!PretentInternet
network 0.0.0.0
ip route 0.0.0.0 0.0.0.0 null 0
ip route 10.0.0.0 255.0.0.0 208.8.8.1


@I3
conf t
router bgp 3
bgp log-neighbor-changes
neighbor 209.9.9.1 remote-as 1
neighbor 35.3.5.5 remote-as 45
neighbor 32.3.2.2 remote-as 2
network 209.9.9.0 mask 255.255.255.0
network 35.3.5.0 mask 255.255.255.0
network 32.3.2.0 mask 255.255.255.0

!PretentInternet
network 0.0.0.0
ip route 0.0.0.0 0.0.0.0 null 0
ip route 10.0.0.0 255.0.0.0 209.9.9.1

@GoogleDNS

conf t
router bgp 45
bgp log-neighbor-changes
neighbor 45.4.5.4 remote-as 45
neighbor 35.3.5.3 remote-as 3
neighbor 25.2.5.2 remote-as 2
network 45.4.5.0 mask 255.255.255.0
network 35.3.5.0 mask 255.255.255.0
network 25.2.5.0 mask 255.255.255.0
network 8.8.8.8 mask 255.255.255.255

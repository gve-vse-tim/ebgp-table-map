# Normal

## Commands

show ip route
show bgp ipv4 unicast
show bgp ipv4 unicast 10.10.10.0/24
show bgp ipv4 unicast 11.11.11.0/24
show bgp ipv4 unicast 33.33.33.0/24

## 

nx-osv9000-4# show ip route
IP Route Table for VRF "default"
'*' denotes best ucast next-hop
'**' denotes best mcast next-hop
'[x/y]' denotes [preference/metric]
'%<string>' in via output denotes VRF <string>

0.0.0.0/0, ubest/mbest: 1/0
    *via 2.2.2.2, [20/0], 00:00:26, bgp-65004, external, tag 65002
1.1.1.1/32, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/41], 23:19:47, ospf-1, intra
2.2.2.2/32, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/41], 23:19:24, ospf-1, intra
3.3.3.3/32, ubest/mbest: 2/0
    *via 192.168.2.2, Eth1/1, [110/81], 03:16:58, ospf-1, intra
    *via 192.168.3.2, Eth1/2, [110/81], 03:16:58, ospf-1, intra
4.4.4.4/32, ubest/mbest: 2/0, attached
    *via 4.4.4.4, Lo0, [0/0], 23:20:49, local
    *via 4.4.4.4, Lo0, [0/0], 23:20:49, direct
10.10.10.0/24, ubest/mbest: 1/0
    *via 2.2.2.2, [20/0], 00:00:26, bgp-65004, external, tag 65002
11.11.11.0/24, ubest/mbest: 1/0
    *via 1.1.1.1, [20/0], 00:00:26, bgp-65004, external, tag 65001
33.33.33.0/24, ubest/mbest: 1/0
    *via 2.2.2.2, [20/0], 00:00:26, bgp-65004, external, tag 65002
192.168.0.0/30, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/80], 03:26:26, ospf-1, intra
192.168.1.0/30, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/80], 03:17:05, ospf-1, intra
192.168.2.0/30, ubest/mbest: 1/0, attached
    *via 192.168.2.1, Eth1/1, [0/0], 23:20:49, direct
192.168.2.1/32, ubest/mbest: 1/0, attached
    *via 192.168.2.1, Eth1/1, [0/0], 23:20:49, local
192.168.3.0/30, ubest/mbest: 1/0, attached
    *via 192.168.3.1, Eth1/2, [0/0], 23:20:49, direct
192.168.3.1/32, ubest/mbest: 1/0, attached
    *via 192.168.3.1, Eth1/2, [0/0], 23:20:49, local

nx-osv9000-4# show bgp ipv4 unicast
BGP routing table information for VRF default, address family IPv4 Unicast
BGP table version is 123, Local Router ID is 4.4.4.4
Status: s-suppressed, x-deleted, S-stale, d-dampened, h-history, *-valid, >-best
Path type: i-internal, e-external, c-confed, l-local, a-aggregate, r-redist, I-injected
Origin codes: i - IGP, e - EGP, ? - incomplete, | - multipath, & - backup

   Network            Next Hop            Metric     LocPrf     Weight Path
*>e0.0.0.0/0          2.2.2.2                                        0 65002 65003 i
* e                   1.1.1.1                                        0 65001 65003 i
* e10.10.10.0/24      1.1.1.1                                        0 65001 65003 i
*>e                   2.2.2.2                                        0 65002 65003 i
*>e11.11.11.0/24      1.1.1.1                                        0 65001 65003 i
* e                   2.2.2.2                                        0 65002 65003 i
* e33.33.33.0/24      1.1.1.1                                        0 65001 65003 i
*>e                   2.2.2.2                                        0 65002 65003 i

nx-osv9000-4# show bgp ipv4 unicast 10.10.10.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 10.10.10.0/24, version 121
Paths: (2 available, best #2)
Flags: (0x08001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW
Multipath: eBGP

  Path type: external, path is valid, received and used, not best reason: newer EBGP path, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Advertised path-id 1
  Path type: external, path is valid, received and used, is best path, no labeled nexthop, in rib
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    1.1.1.1        

nx-osv9000-4# show bgp ipv4 unicast 11.11.11.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 11.11.11.0/24, version 122
Paths: (2 available, best #1)
Flags: (0x8008001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW
Multipath: eBGP

  Advertised path-id 1
  Path type: external, path is valid, received and used, is best path, no labeled nexthop, in rib
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Path type: external, path is valid, received and used, not best reason: newer EBGP path, no labeled nexthop
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    2.2.2.2        

nx-osv9000-4# show bgp ipv4 unicast 33.33.33.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 33.33.33.0/24, version 123
Paths: (2 available, best #2)
Flags: (0x08001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW
Multipath: eBGP

  Path type: external, path is valid, received and used, not best reason: newer EBGP path, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Advertised path-id 1
  Path type: external, path is valid, received and used, is best path, no labeled nexthop, in rib
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    1.1.1.1        

## Enable table-map

router bgp 65004
  address-family ipv4 unicast
    table-map adjust_distance
  exit
exit

nx-osv9000-4(config-router-af)# 2019 Sep 28 00:13:47.677797 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 1.1.1.1 (#135) 
2019 Sep 28 00:13:47.677854 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#139) Finished update run for peer 1.1.1.1 (#139) 
2019 Sep 28 00:13:47.678032 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 2.2.2.2 (#135) 
2019 Sep 28 00:13:47.678047 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#139) Finished update run for peer 2.2.2.2 (#139) 

nx-osv9000-4# show ip route
IP Route Table for VRF "default"
'*' denotes best ucast next-hop
'**' denotes best mcast next-hop
'[x/y]' denotes [preference/metric]
'%<string>' in via output denotes VRF <string>

0.0.0.0/0, ubest/mbest: 1/0
    *via 2.2.2.2, [20/0], 00:00:59, bgp-65004, external, tag 65002
1.1.1.1/32, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/41], 23:22:58, ospf-1, intra
2.2.2.2/32, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/41], 23:22:35, ospf-1, intra
3.3.3.3/32, ubest/mbest: 2/0
    *via 192.168.2.2, Eth1/1, [110/81], 03:20:09, ospf-1, intra
    *via 192.168.3.2, Eth1/2, [110/81], 03:20:09, ospf-1, intra
4.4.4.4/32, ubest/mbest: 2/0, attached
    *via 4.4.4.4, Lo0, [0/0], 23:24:00, local
    *via 4.4.4.4, Lo0, [0/0], 23:24:00, direct
10.10.10.0/24, ubest/mbest: 1/0
    *via 2.2.2.2, [35/0], 00:00:59, bgp-65004, external, tag 65002
11.11.11.0/24, ubest/mbest: 1/0
    *via 1.1.1.1, [20/0], 00:00:59, bgp-65004, external, tag 65001
33.33.33.0/24, ubest/mbest: 1/0
    *via 2.2.2.2, [35/0], 00:00:59, bgp-65004, external, tag 65002
192.168.0.0/30, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/80], 03:29:37, ospf-1, intra
192.168.1.0/30, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/80], 03:20:16, ospf-1, intra
192.168.2.0/30, ubest/mbest: 1/0, attached
    *via 192.168.2.1, Eth1/1, [0/0], 23:24:00, direct
192.168.2.1/32, ubest/mbest: 1/0, attached
    *via 192.168.2.1, Eth1/1, [0/0], 23:24:00, local
192.168.3.0/30, ubest/mbest: 1/0, attached
    *via 192.168.3.1, Eth1/2, [0/0], 23:24:00, direct
192.168.3.1/32, ubest/mbest: 1/0, attached
    *via 192.168.3.1, Eth1/2, [0/0], 23:24:00, local

nx-osv9000-4# show bgp ipv4 unicast
BGP routing table information for VRF default, address family IPv4 Unicast
BGP table version is 139, Local Router ID is 4.4.4.4
Status: s-suppressed, x-deleted, S-stale, d-dampened, h-history, *-valid, >-best
Path type: i-internal, e-external, c-confed, l-local, a-aggregate, r-redist, I-injected
Origin codes: i - IGP, e - EGP, ? - incomplete, | - multipath, & - backup

   Network            Next Hop            Metric     LocPrf     Weight Path
*>e0.0.0.0/0          2.2.2.2                                        0 65002 65003 i
* e                   1.1.1.1                                        0 65001 65003 i
* e10.10.10.0/24      1.1.1.1                                        0 65001 65003 i
*>e                   2.2.2.2                                        0 65002 65003 i
*>e11.11.11.0/24      1.1.1.1                                        0 65001 65003 i
* e                   2.2.2.2                                        0 65002 65003 i
* e33.33.33.0/24      1.1.1.1                                        0 65001 65003 i
*>e                   2.2.2.2                                        0 65002 65003 i

nx-osv9000-4# show bgp ipv4 unicast 10.10.10.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 10.10.10.0/24, version 137
Paths: (2 available, best #2)
Flags: (0x08001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW
Multipath: eBGP

  Path type: external, path is valid, received and used, not best reason: newer EBGP path, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Advertised path-id 1
  Path type: external, path is valid, received and used, is best path, no labeled nexthop, in rib
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    1.1.1.1        

nx-osv9000-4# show bgp ipv4 unicast 11.11.11.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 11.11.11.0/24, version 138
Paths: (2 available, best #1)
Flags: (0x08001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW
Multipath: eBGP

  Advertised path-id 1
  Path type: external, path is valid, received and used, is best path, no labeled nexthop, in rib
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Path type: external, path is valid, received and used, not best reason: newer EBGP path, no labeled nexthop
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    2.2.2.2        

nx-osv9000-4# show bgp ipv4 unicast 33.33.33.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 33.33.33.0/24, version 139
Paths: (2 available, best #2)
Flags: (0x08001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW
Multipath: eBGP

  Path type: external, path is valid, received and used, not best reason: newer EBGP path, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Advertised path-id 1
  Path type: external, path is valid, received and used, is best path, no labeled nexthop, in rib
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    1.1.1.1        


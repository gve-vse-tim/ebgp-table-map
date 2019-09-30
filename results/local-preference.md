# Normal

## Commands

show ip route
show bgp ipv4 unicast
show bgp ipv4 unicast 10.10.10.0/24
show bgp ipv4 unicast 11.11.11.0/24
show bgp ipv4 unicast 33.33.33.0/24

## FIB (routing table)

nx-osv9000-4# show ip route

IP Route Table for VRF "default"
'*' denotes best ucast next-hop
'**' denotes best mcast next-hop
'[x/y]' denotes [preference/metric]
'%<string>' in via output denotes VRF <string>

1.1.1.1/32, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/41], 19:33:44, ospf-1, intra
2.2.2.2/32, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/41], 19:33:21, ospf-1, intra
3.3.3.3/32, ubest/mbest: 2/0
    *via 192.168.2.2, Eth1/1, [110/81], 18:35:48, ospf-1, intra
    *via 192.168.3.2, Eth1/2, [110/81], 18:35:48, ospf-1, intra
4.4.4.4/32, ubest/mbest: 2/0, attached
    *via 4.4.4.4, Lo0, [0/0], 19:34:46, local
    *via 4.4.4.4, Lo0, [0/0], 19:34:46, direct
10.10.10.0/24, ubest/mbest: 1/0
    *via 2.2.2.2, [20/0], 18:24:17, bgp-65004, external, tag 65002
11.11.11.0/24, ubest/mbest: 1/0
    *via 1.1.1.1, [20/0], 18:24:17, bgp-65004, external, tag 65001
33.33.33.0/24, ubest/mbest: 1/0
    *via 2.2.2.2, [20/0], 18:24:17, bgp-65004, external, tag 65002
192.168.0.0/30, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/80], 18:36:01, ospf-1, intra
192.168.1.0/30, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/80], 19:34:34, ospf-1, intra
192.168.2.0/30, ubest/mbest: 1/0, attached
    *via 192.168.2.1, Eth1/1, [0/0], 19:34:46, direct
192.168.2.1/32, ubest/mbest: 1/0, attached
    *via 192.168.2.1, Eth1/1, [0/0], 19:34:46, local
192.168.3.0/30, ubest/mbest: 1/0, attached
    *via 192.168.3.1, Eth1/2, [0/0], 19:34:46, direct
192.168.3.1/32, ubest/mbest: 1/0, attached
    *via 192.168.3.1, Eth1/2, [0/0], 19:34:46, local

## BGP RIB

nx-osv9000-4# show bgp ipv4 unicast 

BGP routing table information for VRF default, address family IPv4 Unicast
BGP table version is 47, Local Router ID is 4.4.4.4
Status: s-suppressed, x-deleted, S-stale, d-dampened, h-history, *-valid, >-best
Path type: i-internal, e-external, c-confed, l-local, a-aggregate, r-redist, I-injected
Origin codes: i - IGP, e - EGP, ? - incomplete, | - multipath, & - backup

   Network            Next Hop            Metric     LocPrf     Weight Path
*>e10.10.10.0/24      2.2.2.2                           150          0 65002 65003 i
* e                   1.1.1.1                            50          0 65001 65003 i
* e11.11.11.0/24      2.2.2.2                            50          0 65002 65003 i
*>e                   1.1.1.1                           150          0 65001 65003 i
*>e33.33.33.0/24      2.2.2.2                           150          0 65002 65003 i
* e                   1.1.1.1                            50          0 65001 65003 i

## BGP NLRI

nx-osv9000-4# show bgp ipv4 unicast 10.10.10.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 10.10.10.0/24, version 45
Paths: (4 available, best #1)
Flags: (0x8008001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW

  Advertised path-id 1
  Path type: external, path is valid, is best path, no labeled nexthop, in rib
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 150, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path type: external, path is valid, not best reason: Local Preference, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 50, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    1.1.1.1        

nx-osv9000-4# show bgp ipv4 unicast 11.11.11.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 11.11.11.0/24, version 46
Paths: (4 available, best #3)
Flags: (0x8008001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW

  Path type: external, path is valid, not best reason: Local Preference, no labeled nexthop
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 50, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Advertised path-id 1
  Path type: external, path is valid, is best path, no labeled nexthop, in rib
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 150, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    2.2.2.2        

nx-osv9000-4# show bgp ipv4 unicast 33.33.33.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 33.33.33.0/24, version 47
Paths: (4 available, best #1)
Flags: (0x8008001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW

  Advertised path-id 1
  Path type: external, path is valid, is best path, no labeled nexthop, in rib
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 150, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path type: external, path is valid, not best reason: Local Preference, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 50, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    1.1.1.1        

# Simulate path failure (SW1 Eth1/1 -> SW3 Eth1/1)

nx-osv9000-4# debug bgp updates 
nx-osv9000-4# terminal monitor

nx-osv9000-1# conf t
nx-osv9000-1(config)# int eth1/1
nx-osv9000-1(config-if)# shut
nx-osv9000-1(config-if)# end

2019 Sep 27 20:41:54.459799 bgp:  [5446] (default) UPD: Received UPDATE message from 1.1.1.1 
2019 Sep 27 20:41:54.459935 bgp:  [5446] (default) UPD: 1.1.1.1 parsed UPDATE message from peer, len 42 , withdraw len 0, attr len 19, nlri len 0 
2019 Sep 27 20:41:54.459977 bgp:  [5446] (default) UPD: Attr code 15, length 15, Mp-unreach 
2019 Sep 27 20:41:54.460285 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received withdrawal for 11.11.11.0/24 from peer 1.1.1.1
2019 Sep 27 20:41:54.460321 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received withdrawal for 10.10.10.0/24 from peer 1.1.1.1
2019 Sep 27 20:41:54.460436 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received withdrawal for 33.33.33.0/24 from peer 1.1.1.1
2019 Sep 27 20:41:54.465986 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 1.1.1.1 (#51) 
2019 Sep 27 20:41:54.466096 bgp:  [5446] (default) UPD: [IPv4 Unicast] consider sending 11.11.11.0/24 to peer 1.1.1.1, path-id 1, best-ext is off
2019 Sep 27 20:41:54.466144 bgp:  [5446] (default) UPD: 1.1.1.1 Sending attr code 1, length 1, Origin: IGP 
2019 Sep 27 20:41:54.466184 bgp:  [5446] (default) UPD: 1.1.1.1 Sending attr code 2, length 14, AS-Path: <65004 65002 65003 > 
2019 Sep 27 20:41:54.466289 bgp:  [5446] (default) UPD: 1.1.1.1 Sending attr code 14, length 13, Mp-reach 
2019 Sep 27 20:41:54.466318 bgp:  [5446] (default) UPD: 1.1.1.1 Sending nexthop address 4.4.4.4 length 4 
2019 Sep 27 20:41:54.466346 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 Created UPD msg (len 61) with prefix 11.11.11.0/24 ( Installed in HW) path-id 1 for peer 
2019 Sep 27 20:41:54.466378 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1: walked 0 nodes and packed 0/0 prefixes (61 bytes) 
2019 Sep 27 20:41:54.466413 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#52) Finished update run for peer 1.1.1.1 (#52) 
2019 Sep 27 20:41:54.466569 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 2.2.2.2 (#51) 
2019 Sep 27 20:41:54.466606 bgp:  [5446] (default) UPD: [IPv4 Unicast] consider sending 11.11.11.0/24 to peer 2.2.2.2, path-id 1, best-ext is off
2019 Sep 27 20:41:54.466632 bgp:  [5446] (default) UPD: [IPv4 Unicast] 2.2.2.2 11.11.11.0/24 path-id 1 not sent to peer due to: advertising peer 
2019 Sep 27 20:41:54.466661 bgp:  [5446] (default) UPD: [IPv4 Unicast] 2.2.2.2 Created withdrawal (len 34) with prefix 11.11.11.0/24 path-id 1 for peer 
2019 Sep 27 20:41:54.466690 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#52) Finished update run for peer 2.2.2.2 (#52) 

nx-osv9000-4# show ip route
IP Route Table for VRF "default"
'*' denotes best ucast next-hop
'**' denotes best mcast next-hop
'[x/y]' denotes [preference/metric]
'%<string>' in via output denotes VRF <string>

1.1.1.1/32, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/41], 19:52:49, ospf-1, intra
2.2.2.2/32, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/41], 19:52:26, ospf-1, intra
3.3.3.3/32, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/81], 00:03:04, ospf-1, intra
4.4.4.4/32, ubest/mbest: 2/0, attached
    *via 4.4.4.4, Lo0, [0/0], 19:53:51, local
    *via 4.4.4.4, Lo0, [0/0], 19:53:51, direct
10.10.10.0/24, ubest/mbest: 1/0
    *via 2.2.2.2, [20/0], 18:43:22, bgp-65004, external, tag 65002
11.11.11.0/24, ubest/mbest: 1/0
    *via 2.2.2.2, [20/0], 00:02:43, bgp-65004, external, tag 65002
33.33.33.0/24, ubest/mbest: 1/0
    *via 2.2.2.2, [20/0], 18:43:22, bgp-65004, external, tag 65002
192.168.0.0/30, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/120], 00:03:04, ospf-1, intra
192.168.1.0/30, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/80], 19:53:39, ospf-1, intra
192.168.2.0/30, ubest/mbest: 1/0, attached
    *via 192.168.2.1, Eth1/1, [0/0], 19:53:51, direct
192.168.2.1/32, ubest/mbest: 1/0, attached
    *via 192.168.2.1, Eth1/1, [0/0], 19:53:51, local
192.168.3.0/30, ubest/mbest: 1/0, attached
    *via 192.168.3.1, Eth1/2, [0/0], 19:53:51, direct
192.168.3.1/32, ubest/mbest: 1/0, attached
    *via 192.168.3.1, Eth1/2, [0/0], 19:53:51, local

nx-osv9000-4# show bgp ipv4 unicast
BGP routing table information for VRF default, address family IPv4 Unicast
BGP table version is 52, Local Router ID is 4.4.4.4
Status: s-suppressed, x-deleted, S-stale, d-dampened, h-history, *-valid, >-best
Path type: i-internal, e-external, c-confed, l-local, a-aggregate, r-redist, I-injected
Origin codes: i - IGP, e - EGP, ? - incomplete, | - multipath, & - backup

   Network            Next Hop            Metric     LocPrf     Weight Path
*>e10.10.10.0/24      2.2.2.2                           150          0 65002 65003 i
*>e11.11.11.0/24      2.2.2.2                            50          0 65002 65003 i
*>e33.33.33.0/24      2.2.2.2                           150          0 65002 65003 i

nx-osv9000-4# show bgp ipv4 unicast 10.10.10.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 10.10.10.0/24, version 49
Paths: (2 available, best #1)
Flags: (0x8008001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW

  Advertised path-id 1
  Path type: external, path is valid, is best path, no labeled nexthop, in rib
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 150, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    1.1.1.1        

nx-osv9000-4# show bgp ipv4 unicast 11.11.11.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 11.11.11.0/24, version 52
Paths: (2 available, best #1)
Flags: (0x8008001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW

  Advertised path-id 1
  Path type: external, path is valid, is best path, no labeled nexthop, in rib
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 50, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    1.1.1.1        

nx-osv9000-4# show bgp ipv4 unicast 33.33.33.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 33.33.33.0/24, version 50
Paths: (2 available, best #1)
Flags: (0x8008001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW

  Advertised path-id 1
  Path type: external, path is valid, is best path, no labeled nexthop, in rib
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 150, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65002 65003 , path sourced external to AS
    2.2.2.2 (metric 41) from 2.2.2.2 (2.2.2.2)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    1.1.1.1        

## Restore path 1.1.1.1

nx-osv9000-4# 

2019 Sep 27 20:46:11.472092 bgp:  [5446] (default) UPD: Received UPDATE message from 1.1.1.1 
2019 Sep 27 20:46:11.472140 bgp:  [5446] (default) UPD: 1.1.1.1 parsed UPDATE message from peer, len 65 , withdraw len 0, attr len 42, nlri len 0 
2019 Sep 27 20:46:11.472160 bgp:  [5446] (default) UPD: Attr code 1, length 1, Origin: IGP 
2019 Sep 27 20:46:11.472178 bgp:  [5446] (default) UPD: Peer 1.1.1.1 nexthop length in MP reach: 4 
2019 Sep 27 20:46:11.472260 bgp:  [5446] (default) UPD: Recvd NEXTHOP 1.1.1.1 
2019 Sep 27 20:46:11.472272 bgp:  [5446] (default) UPD: Attr code 14, length 21, Mp-reach 
2019 Sep 27 20:46:11.472339 bgp:  [5446] (default) UPD: 1.1.1.1 Received attr code 2, length 10, AS-Path: <65001 65003 > 
2019 Sep 27 20:46:11.472395 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received prefix 10.10.10.0/24 from peer 1.1.1.1, origin 0, next hop 1.1.1.1, localpref 0, med 0
2019 Sep 27 20:46:11.472429 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 Inbound route-map prefer_router_one, action permit 
2019 Sep 27 20:46:11.472949 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received prefix 11.11.11.0/24 from peer 1.1.1.1, origin 0, next hop 1.1.1.1, localpref 0, med 0
2019 Sep 27 20:46:11.472970 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 Inbound route-map prefer_router_one, action permit 
2019 Sep 27 20:46:11.473133 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received prefix 33.33.33.0/24 from peer 1.1.1.1, origin 0, next hop 1.1.1.1, localpref 0, med 0
2019 Sep 27 20:46:11.473213 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 Inbound route-map prefer_router_one, action permit 
2019 Sep 27 20:46:11.479414 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 1.1.1.1 (#52) 
2019 Sep 27 20:46:11.479438 bgp:  [5446] (default) UPD: [IPv4 Unicast] consider sending 11.11.11.0/24 to peer 1.1.1.1, path-id 1, best-ext is off
2019 Sep 27 20:46:11.479453 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 11.11.11.0/24 path-id 1 not sent to peer due to: advertising peer 
2019 Sep 27 20:46:11.479471 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 Created withdrawal (len 34) with prefix 11.11.11.0/24 path-id 1 for peer 
2019 Sep 27 20:46:11.479494 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#55) Finished update run for peer 1.1.1.1 (#55) 
2019 Sep 27 20:46:11.479652 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 2.2.2.2 (#52) 
2019 Sep 27 20:46:11.479664 bgp:  [5446] (default) UPD: [IPv4 Unicast] consider sending 11.11.11.0/24 to peer 2.2.2.2, path-id 1, best-ext is off
2019 Sep 27 20:46:11.479684 bgp:  [5446] (default) UPD: 2.2.2.2 Sending attr code 1, length 1, Origin: IGP 
2019 Sep 27 20:46:11.479709 bgp:  [5446] (default) UPD: 2.2.2.2 Sending attr code 2, length 14, AS-Path: <65004 65001 65003 > 
2019 Sep 27 20:46:11.479791 bgp:  [5446] (default) UPD: 2.2.2.2 Sending attr code 14, length 13, Mp-reach 
2019 Sep 27 20:46:11.479803 bgp:  [5446] (default) UPD: 2.2.2.2 Sending nexthop address 4.4.4.4 length 4 

## Take down SW2 path (SW2 Eth1/1->SW3 Eth1/2)

nx-osv9000-2# conf t
Enter configuration commands, one per line. End with CNTL/Z.
nx-osv9000-2(config)# int eth1/1
nx-osv9000-2(config-if)# shut
nx-osv9000-2(config-if)# end

nx-osv9000-4# 
2019 Sep 27 20:53:05.032823 bgp:  [5446] (default) UPD: Received UPDATE message from 2.2.2.2 
2019 Sep 27 20:53:05.032924 bgp:  [5446] (default) UPD: 2.2.2.2 parsed UPDATE message from peer, len 38 , withdraw len 0, attr len 15, nlri len 0 
2019 Sep 27 20:53:05.032946 bgp:  [5446] (default) UPD: Attr code 15, length 11, Mp-unreach 
2019 Sep 27 20:53:05.033191 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received withdrawal for 10.10.10.0/24 from peer 2.2.2.2
2019 Sep 27 20:53:05.033331 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received withdrawal for 33.33.33.0/24 from peer 2.2.2.2
2019 Sep 27 20:53:05.038755 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 1.1.1.1 (#55) 
2019 Sep 27 20:53:05.038799 bgp:  [5446] (default) UPD: [IPv4 Unicast] consider sending 10.10.10.0/24 to peer 1.1.1.1, path-id 1, best-ext is off
2019 Sep 27 20:53:05.038834 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 10.10.10.0/24 path-id 1 not sent to peer due to: advertising peer 
2019 Sep 27 20:53:05.038868 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 Created withdrawal (len 34) with prefix 10.10.10.0/24 path-id 1 for peer 
2019 Sep 27 20:53:05.038896 bgp:  [5446] (default) UPD: [IPv4 Unicast] consider sending 33.33.33.0/24 to peer 1.1.1.1, path-id 1, best-ext is off
2019 Sep 27 20:53:05.038921 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 33.33.33.0/24 path-id 1 not sent to peer due to: advertising peer 
2019 Sep 27 20:53:05.038998 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#57) Finished update run for peer 1.1.1.1 (#57) 
2019 Sep 27 20:53:05.039186 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 2.2.2.2 (#55) 
2019 Sep 27 20:53:05.039271 bgp:  [5446] (default) UPD: [IPv4 Unicast] consider sending 10.10.10.0/24 to peer 2.2.2.2, path-id 1, best-ext is off
2019 Sep 27 20:53:05.039312 bgp:  [5446] (default) UPD: 2.2.2.2 Sending attr code 1, length 1, Origin: IGP 
2019 Sep 27 20:53:05.039357 bgp:  [5446] (default) UPD: 2.2.2.2 Sending attr code 2, length 14, AS-Path: <65004 65001 65003 > 
2019 Sep 27 20:53:05.039462 bgp:  [5446] (default) UPD: 2.2.2.2 Sending attr code 14, length 13, Mp-reach 
2019 Sep 27 20:53:05.039490 bgp:  [5446] (default) UPD: 2.2.2.2 Sending nexthop address 4.4.4.4 length 4 
2019 Sep 27 20:53:05.039516 bgp:  [5446] (default) UPD: [IPv4 Unicast] 2.2.2.2 Created UPD msg (len 61) with prefix 10.10.10.0/24 ( Installed in HW) path-id 1 for peer 
2019 Sep 27 20:53:05.039548 bgp:  [5446] (default) UPD: [IPv4 Unicast] 2.2.2.2 Packed UPD msg with prefix 33.33.33.0/24 ( Installed in HW) path-id 1 for peer 
2019 Sep 27 20:53:05.039574 bgp:  [5446] (default) UPD: [IPv4 Unicast] 2.2.2.2: walked 1 nodes and packed 1/0 prefixes (65 bytes) 
2019 Sep 27 20:53:05.039603 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#57) Finished update run for peer 2.2.2.2 (#57) 
2019 Sep 27 20:53:05.039790 bgp:  [5446] (default) UPD: Received UPDATE message from 2.2.2.2 
2019 Sep 27 20:53:05.039828 bgp:  [5446] (default) UPD: 2.2.2.2 parsed UPDATE message from peer, len 34 , withdraw len 0, attr len 11, nlri len 0 
2019 Sep 27 20:53:05.039854 bgp:  [5446] (default) UPD: Attr code 15, length 7, Mp-unreach 
2019 Sep 27 20:53:05.039889 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received withdrawal for 11.11.11.0/24 from peer 2.2.2.2

nx-osv9000-4# show ip route
IP Route Table for VRF "default"
'*' denotes best ucast next-hop
'**' denotes best mcast next-hop
'[x/y]' denotes [preference/metric]
'%<string>' in via output denotes VRF <string>

1.1.1.1/32, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/41], 20:01:59, ospf-1, intra
2.2.2.2/32, ubest/mbest: 1/0
    *via 192.168.3.2, Eth1/2, [110/41], 20:01:36, ospf-1, intra
3.3.3.3/32, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/81], 00:00:52, ospf-1, intra
4.4.4.4/32, ubest/mbest: 2/0, attached
    *via 4.4.4.4, Lo0, [0/0], 20:03:01, local
    *via 4.4.4.4, Lo0, [0/0], 20:03:01, direct
10.10.10.0/24, ubest/mbest: 1/0
    *via 1.1.1.1, [20/0], 00:00:43, bgp-65004, external, tag 65001
11.11.11.0/24, ubest/mbest: 1/0
    *via 1.1.1.1, [20/0], 00:07:36, bgp-65004, external, tag 65001
33.33.33.0/24, ubest/mbest: 1/0
    *via 1.1.1.1, [20/0], 00:00:43, bgp-65004, external, tag 65001
192.168.0.0/30, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/80], 00:08:38, ospf-1, intra
192.168.1.0/30, ubest/mbest: 1/0
    *via 192.168.2.2, Eth1/1, [110/120], 00:00:52, ospf-1, intra
192.168.2.0/30, ubest/mbest: 1/0, attached
    *via 192.168.2.1, Eth1/1, [0/0], 20:03:01, direct
192.168.2.1/32, ubest/mbest: 1/0, attached
    *via 192.168.2.1, Eth1/1, [0/0], 20:03:01, local
192.168.3.0/30, ubest/mbest: 1/0, attached
    *via 192.168.3.1, Eth1/2, [0/0], 20:03:01, direct
192.168.3.1/32, ubest/mbest: 1/0, attached
    *via 192.168.3.1, Eth1/2, [0/0], 20:03:01, local

nx-osv9000-4# show bgp ipv4 unicast
BGP routing table information for VRF default, address family IPv4 Unicast
BGP table version is 57, Local Router ID is 4.4.4.4
Status: s-suppressed, x-deleted, S-stale, d-dampened, h-history, *-valid, >-best
Path type: i-internal, e-external, c-confed, l-local, a-aggregate, r-redist, I-injected
Origin codes: i - IGP, e - EGP, ? - incomplete, | - multipath, & - backup

   Network            Next Hop            Metric     LocPrf     Weight Path
*>e10.10.10.0/24      1.1.1.1                            50          0 65001 65003 i
*>e11.11.11.0/24      1.1.1.1                           150          0 65001 65003 i
*>e33.33.33.0/24      1.1.1.1                            50          0 65001 65003 i

nx-osv9000-4# show bgp ipv4 unicast 10.10.10.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 10.10.10.0/24, version 56
Paths: (2 available, best #1)
Flags: (0x8008001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW

  Advertised path-id 1
  Path type: external, path is valid, is best path, no labeled nexthop, in rib
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 50, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    2.2.2.2        

nx-osv9000-4# show bgp ipv4 unicast 11.11.11.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 11.11.11.0/24, version 55
Paths: (2 available, best #1)
Flags: (0x8008001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW

  Advertised path-id 1
  Path type: external, path is valid, is best path, no labeled nexthop, in rib
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 150, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    2.2.2.2        

nx-osv9000-4# show bgp ipv4 unicast 33.33.33.0/24
BGP routing table information for VRF default, address family IPv4 Unicast
BGP routing table entry for 33.33.33.0/24, version 57
Paths: (2 available, best #1)
Flags: (0x8008001a) (high32 00000000) on xmit-list, is in urib, is best urib route, is in HW

  Advertised path-id 1
  Path type: external, path is valid, is best path, no labeled nexthop, in rib
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 50, weight 0

  Path type: external, path is valid, received only, no labeled nexthop
  AS-Path: 65001 65003 , path sourced external to AS
    1.1.1.1 (metric 41) from 1.1.1.1 (1.1.1.1)
      Origin IGP, MED not set, localpref 100, weight 0

  Path-id 1 advertised to peers:
    2.2.2.2        

## Restore path

nx-osv9000-4# 2019 Sep 27 20:54:44.446905 bgp:  [5446] (default) UPD: Received UPDATE message from 2.2.2.2 
2019 Sep 27 20:54:44.447039 bgp:  [5446] (default) UPD: 2.2.2.2 parsed UPDATE message from peer, len 65 , withdraw len 0, attr len 42, nlri len 0 
2019 Sep 27 20:54:44.447064 bgp:  [5446] (default) UPD: Attr code 1, length 1, Origin: IGP 
2019 Sep 27 20:54:44.447089 bgp:  [5446] (default) UPD: Peer 2.2.2.2 nexthop length in MP reach: 4 
2019 Sep 27 20:54:44.447187 bgp:  [5446] (default) UPD: Recvd NEXTHOP 2.2.2.2 
2019 Sep 27 20:54:44.447207 bgp:  [5446] (default) UPD: Attr code 14, length 21, Mp-reach 
2019 Sep 27 20:54:44.447241 bgp:  [5446] (default) UPD: 2.2.2.2 Received attr code 2, length 10, AS-Path: <65002 65003 > 
2019 Sep 27 20:54:44.447317 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received prefix 10.10.10.0/24 from peer 2.2.2.2, origin 0, next hop 2.2.2.2, localpref 0, med 0
2019 Sep 27 20:54:44.447362 bgp:  [5446] (default) UPD: [IPv4 Unicast] 2.2.2.2 Inbound route-map prefer_router_two, action permit 
2019 Sep 27 20:54:44.448185 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received prefix 11.11.11.0/24 from peer 2.2.2.2, origin 0, next hop 2.2.2.2, localpref 0, med 0
2019 Sep 27 20:54:44.448287 bgp:  [5446] (default) UPD: [IPv4 Unicast] 2.2.2.2 Inbound route-map prefer_router_two, action permit 
2019 Sep 27 20:54:44.448568 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received prefix 33.33.33.0/24 from peer 2.2.2.2, origin 0, next hop 2.2.2.2, localpref 0, med 0
2019 Sep 27 20:54:44.448685 bgp:  [5446] (default) UPD: [IPv4 Unicast] 2.2.2.2 Inbound route-map prefer_router_two, action permit 
2019 Sep 27 20:54:44.454252 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 1.1.1.1 (#57) 
2019 Sep 27 20:54:44.454294 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#58) Finished update run for peer 1.1.1.1 (#58) 
2019 Sep 27 20:54:44.454553 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 2.2.2.2 (#57) 
2019 Sep 27 20:54:44.454578 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#58) Finished update run for peer 2.2.2.2 (#58) 
2019 Sep 27 20:54:44.460033 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 1.1.1.1 (#58) 
2019 Sep 27 20:54:44.460090 bgp:  [5446] (default) UPD: [IPv4 Unicast] consider sending 10.10.10.0/24 to peer 1.1.1.1, path-id 1, best-ext is off
2019 Sep 27 20:54:44.460114 bgp:  [5446] (default) UPD: 1.1.1.1 Sending attr code 1, length 1, Origin: IGP 
2019 Sep 27 20:54:44.460140 bgp:  [5446] (default) UPD: 1.1.1.1 Sending attr code 2, length 14, AS-Path: <65004 65002 65003 > 
2019 Sep 27 20:54:44.460216 bgp:  [5446] (default) UPD: 1.1.1.1 Sending attr code 14, length 13, Mp-reach 
2019 Sep 27 20:54:44.460228 bgp:  [5446] (default) UPD: 1.1.1.1 Sending nexthop address 4.4.4.4 length 4 
2019 Sep 27 20:54:44.460241 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 Created UPD msg (len 61) with prefix 10.10.10.0/24 ( Installed in HW) path-id 1 for peer 
2019 Sep 27 20:54:44.460314 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 Packed UPD msg with prefix 33.33.33.0/24 ( Installed in HW) path-id 1 for peer 
2019 Sep 27 20:54:44.460327 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1: walked 1 nodes and packed 1/0 prefixes (65 bytes) 
2019 Sep 27 20:54:44.460349 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#60) Finished update run for peer 1.1.1.1 (#60) 
2019 Sep 27 20:54:44.460516 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 2.2.2.2 (#58) 
2019 Sep 27 20:54:44.460635 bgp:  [5446] (default) UPD: [IPv4 Unicast] 2.2.2.2 Created withdrawal (len 34) with prefix 10.10.10.0/24 path-id 1 for peer 
2019 Sep 27 20:54:44.460656 bgp:  [5446] (default) UPD: [IPv4 Unicast] consider sending 33.33.33.0/24 to peer 2.2.2.2, path-id 1, best-ext is off
2019 Sep 27 20:54:44.460667 bgp:  [5446] (default) UPD: [IPv4 Unicast] 2.2.2.2 33.33.33.0/24 path-id 1 not sent to peer due to: advertising peer 
2019 Sep 27 20:54:44.460682 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#60) Finished update run for peer 2.2.2.2 (#60) 

###  Removed route map for 2.2.2.2 to adjust local preference

nx-osv9000-4(config-router-neighbor-af)# no       route-map prefer_router_two in
nx-osv9000-4(config-router-neighbor-af)# en2019 Sep 27 20:57:59.187034 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 1.1.1.1 (#65) 
2019 Sep 27 20:57:59.187128 bgp:  [5446] (default) UPD: [IPv4 Unicast] consider sending 10.10.10.0/24 to peer 1.1.1.1, path-id 1, best-ext is off
2019 Sep 27 20:57:59.187150 bgp:  [5446] (default) UPD: 1.1.1.1 Sending attr code 1, length 1, Origin: IGP 
2019 Sep 27 20:57:59.187170 bgp:  [5446] (default) UPD: 1.1.1.1 Sending attr code 2, length 14, AS-Path: <65004 65002 65003 > 
2019 Sep 27 20:57:59.187262 bgp:  [5446] (default) UPD: 1.1.1.1 Sending attr code 14, length 13, Mp-reach 
2019 Sep 27 20:57:59.187272 bgp:  [5446] (default) UPD: 1.1.1.1 Sending nexthop address 4.4.4.4 length 4 
2019 Sep 27 20:57:59.187283 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 Created UPD msg (len 61) with prefix 10.10.10.0/24 ( Installed in HW) path-id 1 for peer 
d2019 Sep 27 20:57:59.187296 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1 Packed UPD msg with prefix 33.33.33.0/24 ( Installed in HW) path-id 1 for peer 
2019 Sep 27 20:57:59.187305 bgp:  [5446] (default) UPD: [IPv4 Unicast] 1.1.1.1: walked 1 nodes and packed 1/0 prefixes (65 bytes) 
2019 Sep 27 20:57:59.187357 bgp:  [5446] (default) UPD: [IPv4 Unicast] (#68) Finished update run for peer 1.1.1.1 (#68) 
2019 Sep 27 20:57:59.187476 bgp:  [5446] (default) UPD: [IPv4 Unicast] Starting update run for peer 2.2.2.2 (#65) 
2019 Sep 27 20:57:59.203707 bgp:  [5446] (default) UPD: Received UPDATE message from 2.2.2.2 
2019 Sep 27 20:57:59.203795 bgp:  [5446] (default) UPD: 2.2.2.2 parsed UPDATE message from peer, len 65 , withdraw len 0, attr len 42, nlri len 0 
2019 Sep 27 20:57:59.203815 bgp:  [5446] (default) UPD: Attr code 1, length 1, Origin: IGP 
2019 Sep 27 20:57:59.203837 bgp:  [5446] (default) UPD: Peer 2.2.2.2 nexthop length in MP reach: 4 
2019 Sep 27 20:57:59.203928 bgp:  [5446] (default) UPD: Recvd NEXTHOP 2.2.2.2 
2019 Sep 27 20:57:59.203951 bgp:  [5446] (default) UPD: Attr code 14, length 21, Mp-reach 
2019 Sep 27 20:57:59.203979 bgp:  [5446] (default) UPD: 2.2.2.2 Received attr code 2, length 10, AS-Path: <65002 65003 > 
2019 Sep 27 20:57:59.204046 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received prefix 10.10.10.0/24 from peer 2.2.2.2, origin 0, next hop 2.2.2.2, localpref 0, med 0
2019 Sep 27 20:57:59.204082 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received prefix 33.33.33.0/24 from peer 2.2.2.2, origin 0, next hop 2.2.2.2, localpref 0, med 0
2019 Sep 27 20:57:59.204105 bgp:  [5446] (default) UPD: [IPv4 Unicast] Received prefix 11.11.11.0/24 from peer 2.2.2.2, origin 0, next hop 2.2.2.2, localpref 0, med 0
2019 Sep 27 20:57:59.204126 bgp:  [5446] (default) UPD: Received UPDATE message from 2.2.2.2 


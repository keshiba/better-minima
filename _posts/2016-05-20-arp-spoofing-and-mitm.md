---
layout: post
title: "ARP spoofing: How to prevent ARP spoofing"
author: Keshiba
featured: true
categories: tech
---

ARP spoofing is a technique by which an attacker sends (spoofed) Address Resolution Protocol (ARP) messages onto a local area network.

## Introduction

In computer networking, ARP spoofing, ARP cache poisoning, or ARP poison routing, is a technique by which an attacker sends (spoofed) Address Resolution Protocol (ARP) messages onto a local area network. Generally, the aim is to associate the attacker's MAC address with the IP address of another host, such as the default gateway, causing any traffic meant for that IP address to be sent to the attacker instead.

ARP spoofing may allow an attacker to intercept data frames on a network, modify the traffic, or stop all traffic. Often the attack is used as an opening for other attacks, such as denial of service, man in the middle, or session hijacking attacks.


### ARP vulnerabilities

The Address Resolution Protocol (ARP) is a widely used communications protocol for resolving Internet layer addresses into link layer addresses.

When an Internet Protocol (IP) datagram is sent from one host to another in a local area network, the destination IP address must be resolved to a MAC address for transmission via the data link layer. When another host's IP address is known, and its MAC address is needed, a broadcast packet is sent out on the local network. This packet is known as an ARP request. The destination machine with the IP in the ARP request then responds with an ARP reply that contains the MAC address for that IP.

ARP is a stateless protocol. Network hosts will automatically cache any ARP replies they receive, regardless of whether network hosts requested them. Even ARP entries that have not yet expired will be overwritten when a new ARP reply packet is received. There is no method in the ARP protocol by which a host can authenticate the peer from which the packet originated. This behavior is the vulnerability that allows ARP spoofing to occur.


## Defense

#### Static ARP entries
The simplest form of certification is the use of static, read-only entries for critical services in the ARP cache of a host. IP address-to-MAC address mappings in the local ARP cache may be statically entered. Hosts don't need to transmit ARP requests where such entries exist. While static entries provide some security against spoofing, they result in maintenance efforts as address mappings for all systems in the network must be generated and distributed. This does not scale on a large network since the mapping has to be set for each pair of machines resulting in n2-n ARP entries that have to be configured when n machines are present; On each machine there must be an ARP entry for every other machine on the network; n-1 ARP entries on each of the n machines.

#### ARP spoofing detection and prevention software
Software that detects ARP spoofing generally relies on some form of certification or cross-checking of ARP responses. Uncertified ARP responses are then blocked. These techniques may be integrated with the DHCP server so that both dynamic and static IP addresses are certified. This capability may be implemented in individual hosts or may be integrated into Ethernet switches or other network equipment. The existence of multiple IP addresses associated with a single MAC address may indicate an ARP spoof attack, although there are legitimate uses of such a configuration. In a more passive approach a device listens for ARP replies on a network, and sends a notification via email when an ARP entry changes.

**AntiARP** also provides Windows-based spoofing prevention at the kernel level. ArpStar is a Linux module for kernel 2.6 and Linksys routers that drops invalid packets that violate mapping, and contains an option to repoison/heal.

Some virtualized environment such as KVM also provides security mechanism to prevent MAC spoofing between guest running on the same host.

Additionally some ethernet adapters provides MAC and VLAN anti-spoofing features.

OpenBSD watches passively for hosts impersonating the local host and notifies in case of any attempt to overwrite a permanent entry

#### OS security
Operating systems react differently. Linux ignores unsolicited replies, but, on the other hand, uses responses to requests from other machines to update its cache. Solaris accepts updates on entries only after a timeout. In Microsoft Windows, the behavior of the ARP cache can be configured through several registry entries under `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters`, ArpCacheLife, ArpCacheMinReferenceLife, ArpUseEtherSNAP, ArpTRSingleRoute, ArpAlwaysSourceRoute, ArpRetryCount.

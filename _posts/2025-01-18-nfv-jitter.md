---
layout: post
title: "6G Is coming: why jitter and latency could be our biggest worries?"
date: 2025-01-18 05:00:00
description: Let's talk about virtualization of network components possible issues.
tags: NFV CNF DPDK
categories: network packet-processing
---

### TLDR;

Modern communication networks connect users through a hierarchy of local, metro, and core systems operated by ISPs and cellular network providers. While these networks once relied on specialized hardware for predictable high performance and low power use, the industry is rapidly adopting software‑defined and virtualized architectures on general‑purpose processors. This brings greater flexibility, faster innovation, and scalable throughput but also revives old problems around jitter and latency. Addressing these performance challenges in virtualized environments is becoming a central focus for future network research and design.

#### Understanding How Communication Networks Work

Before diving into current developments, it’s useful to see how communication systems operate from a high level. We are not considering non terrestrial network like satellite communicatio in this view.

A user connects through a device that either sits on a local area network (Ethernet or Wi‑Fi) or attaches to a cellular radio access network (RAN). Both connect to an access or aggregation network in the metropolitan area (MAN), then move through provider core and backbone networks (WAN), and finally traverse peering or transit points to reach other networks and the public internet.

ISPs and cellular network operators interconnect at metropolitan points of presence, internet exchange points, and private peerings—enabling end‑to‑end traffic flow across fixed broadband, cellular, and cloud systems.

#### The Role of Compute in Networking

At the heart of these communication layers lies compute power, which enables efficient, secure data transfer. This compute infrastructure comes in various forms; routers, switches, firewalls, and specialized units for cellular networks.

Traditionally, such components were built on dedicated hardware. The algorithms ran on specialized silicon chips (ASICs or FPGAs) that offered high performance but limited flexibility. Because these chips are expensive and take decades to upgrade, innovation cycles were slow. In contrast, consumer grade general-purpose processors improve yearly, becoming more efficient and capable.

#### From Dedicated Hardware to Virtualization

Special purpose hardware provides predictable, energy-efficient high performance but is rigid. General purpose processors, however, can run varied software written for specific networking tasks. This separation between hardware and software enables faster innovation, easier and greener lifecycle management.

The next evolution is virtualization, running multiple network applications efficiently on shared hardware. Virtualization allows on-demand provisioning and dynamic network behavior based on user needs. Modern virtualization, combined with advances in multicore CPUs and optimized caching, now supports data throughput in the hundreds of gigabits per network interface.

Notable contributions from industry and academia include the [DPDK](https://www.dpdk.org) project and academic research groups such as [SDNLab](https://www2.matlab.nitech.ac.jp/papers/en) at Nagoya Institute of Technology and the [Networked Systems Lab](https://www.kth.se/cs/scs/forskning/network-systems) at KTH, Sweden. Annual DPDK community events frequently showcase new advancements in high-performance networking. Talks and presentation at [DPDK summits](https://www.youtube.com/@dpdkproject/playlists) are released in youtube as well, which makes it very accessable.

#### The Lingering Challenge: Jitter and Latency

While we are chasing the speed, and processing scalibility using general purpose processors, advanced high bandwith NICs, and virtualized technology little to no thoughts is given to the jitter and latency issue much. In the traditional specialized hardware era the jitter issue and latency issues recieved great amount of attention which is many decades ago. Where folkes developed sharding and various specialized technique to counter them. But in such case where much of the context switch like in virtualization was absent, so it was relatively easiser. Now we have hardware virtualization, software virtualization, user space application, accelerator like GPUs, all of these talk to each other thorugh a elaborate procedure calls. Instructions jumps from one to another, sophisticated power and cpu states configurations offered on commodity CPUs hamper the code execution, in such wild west it's hard to have predictive performance hence early sinces of struggle with jitter and latency.

#### Directions for Research and Evaluation

As virtualized network functions continue to scale, their cumulative latency and jitter effects could become significant in production deployments. Research should refocus on quantifying these effects, starting with controlled point-to-point experiments to estimate their network wide impact.

Understanding these emerging performance characteristics will be critical to ensuring that virtualized communication systems remain both flexible and reliable.

### Reference paper

[1] Bhutto, A. B., Kawashima, R., Taenaka, Y., & Kadobayashi, Y. (2024, July). [Meeting latency and jitter demands of beyond 5g networking era: Are cnfs up to the challenge?](https://doi.org/10.1109/COMPSAC61105.2024.00251). In 2024 IEEE 48th Annual Computers, Software, and Applications Conference (COMPSAC) (pp. 1598-1605). IEEE.

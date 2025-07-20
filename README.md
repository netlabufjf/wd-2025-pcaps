# wd-2025-pcaps

Archive of the packet capture (PCAP) files created as part of the evaluation of a 5G simulated environment created by the [free5GC auto deploy](https://github.com/oliveiraleo/free5gc-auto-deploy) tool

The experiment involved executing free5GC alongside a User Equipment (UE) to send five ping requests to Google DNS servers. This process was repeated twice, once for each access type. The captures encompass all packets generated from the initiation of free5GC until its termination, including NF signaling.

## Folder structure

- `3gpp-access`: files generated using [UERANSIM](https://github.com/aligungr/UERANSIM)
- `non3gpp-access`: files generated using [TNGFUE](https://free5gc.org/guide/TNGF/tngfue-installation/)

**Note:** [free5GC](https://github.com/free5gc/free5gc) was used as the 5G Core (5GC) to provide both access types

### File naming pattern

The files use the pattern: `authentication_protocol`-`access_type`-`network_interface`-`context`.pcap

**Example:** 5g_aka-3gpp-enp0s3-free5gc.pcap 

This file was captured in the `enp0s3` (Ethernet) network interface of the free5GC VM, while the UE used 5G AKA as the authentication algorithm

**Example 2:** eap_aka_prime-non3gpp-wlp3s0-tngfue.pcap

This file was captured in the `wlp3s0` (Wi-Fi) network interface of the TNGFUE PC, while the UE used EAP-AKA' as the authentication algorithm

The section below details all the possibilities for each part of the name

## Detailed characteristics description

### Authentication protocol

- `5g_aka`: 5G-AKA
- `eap_aka_prime`: EAP-AKA'

### Access type

- `3gpp`: 5G 3GPP connection
- `non3gpp`: Wi-Fi non-3GPP connection

### Network interface

- `enp0s3`: packets used by the VMs to communicate with the real host (internet access, etc.)
- `lo`: loopback, packets transmitted between the 5GC NFs
- `upfgtp`: packets that leave the 5GC to reach the internet (via UPF)
- `uesimtun0`: virtual network tunnel that allows for UE internet access
- `wlp3s0`: packets used by the PC to communicate with the TNAP
- `greTun0`: virtual network tunnel that allows for non-3GPP UE internet access

### Context

- `free5gc`: simulated 3GPP 5GC running in a VM
- `ueransim`: simulated 3GPP UE running in a VM
- `tngfue`: simulated non-3GPP UE running on a laptop host

## IP addresses

- `127.0.0.x`: free5GC NFs
- `192.168.1.1`: TNAP/Wi-Fi LAN and internet gateway
- `192.168.1.91`: UERANSIM
- `192.168.1.100`: free5GC
- `192.168.1.202`: TNGFUE
- `10.60.0.1`: UE virtual IP* 
- `8.8.8.8`: Google Public DNS

\* 3GPP and non-3GPP, run separately

When you're creating a VNet, use address ranges enumerated in **RFC 1918**. These addresses are for **private, nonroutable address spaces**.

### Private Address Ranges (RFC 1918)

- `10.0.0.0 - 10.255.255.255` (**10/8 prefix**)
- `172.16.0.0 - 172.31.255.255` (**172.16/12 prefix**)
- `192.168.0.0 - 192.168.255.255` (**192.168/16 prefix**)

### Reserved Address Ranges

- `224.0.0.0/4` — Multicast  
- `255.255.255.255/32` — Broadcast  
- `127.0.0.0/8` — Loopback  
- `169.254.0.0/16` — Link-local  
- `168.63.129.16/32` — Internal DNS

Just like in a traditional network, **subnets** allow you to segment your **VNet address space** into segments that are appropriate for the organization's internal network.

The **smallest supported IPv4 subnet** is `/29`, and the **largest** is `/2` (using **CIDR subnet definitions**).  
**IPv6 subnets** must be exactly `/64` in size.

Source: https://learn.microsoft.com/en-gb/training/modules/introduction-to-azure-virtual-networks/2-explore-azure-virtual-networks
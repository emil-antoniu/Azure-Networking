## Configure internet access with Azure Virtual NAT

Azure **Network Address Translation (NAT)** allows internal resources on a private network to share routable IPv4 addresses.

### Key Behaviors

- After NAT is configured, **all UDP and TCP outbound flows** from any VM instance use NAT for internet connectivity.
- NAT **scales automatically** to support dynamic workloads.
- Supports **up to 16 public IP addresses**.
- Uses **Port Network Address Translation (PNAT/PAT)** to provide up to **64,000 concurrent flows** per UDP/TCP protocol.

---

## Limitations

- Supports **IPv4 only** — NAT does not interact with IPv6.
- NAT **cannot span multiple virtual networks**.
- **IP fragmentation is not supported**.

---

**Source:**  
https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-virtual-networks/10-configure-internet-access-azure-virtual-nat

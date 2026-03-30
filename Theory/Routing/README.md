# Routing

## Azure Default System Routes

Whenever a virtual network is created, Azure automatically adds the following **default system routes** to each subnet.

### Default System Routes

| Source  | Address Prefixes        | Next Hop Type     |
|---------|--------------------------|--------------------|
| Default | Unique to the VNet       | Virtual network    |
| Default | 0.0.0.0/0                | Internet           |
| Default | 10.0.0.0/8               | None               |
| Default | 172.16.0.0/12            | None               |
| Default | 192.168.0.0/16           | None               |
| Default | 100.64.0.0/10            | None               |

---

## Optional Default Routes

Azure may add **optional default routes** depending on the capabilities enabled in the virtual network.

| Source                  | Address Prefixes                                                                 | Next Hop Type                 | Subnets Affected                                |
|-------------------------|-----------------------------------------------------------------------------------|-------------------------------|-------------------------------------------------|
| Default                 | Unique to the VNet (e.g., 10.1.0.0/16)                                            | Virtual network peering       | All                                             |
| Virtual network gateway | Prefixes advertised from on‑premises via BGP, or configured in the local gateway | Virtual network gateway       | All                                             |
| Default                 | Multiple                                                                          | VirtualNetworkServiceEndpoint | Only the subnet where the service endpoint is enabled |

---

## User‑Defined Routes (UDR)

You can override Azure’s default routes using **user‑defined routes (UDRs)**.  
This is useful when you need traffic between subnets to pass through a firewall or other appliance.

Key points:

- Each subnet can have **zero or one** associated route table.
- When a route table is associated with a subnet:
  - Its routes **combine with** or **override** Azure’s default routes.
- UDRs allow precise control over traffic flow within a virtual network.

---

**Source:**  
https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-virtual-networks/9-implement-virtual-network-traffic-routing

## Tools to Troubleshoot Routing Problems

To view the IPv4 routing table in Windows PowerShell, run:

`Get-NetRoute -AddressFamily IPv4`

To create a new route, use the `New-NetRoute` cmdlet.  
For example, the following command adds a route for the `10.0.0.0/8` network on interface index `10`, directing traffic to the gateway at `192.168.0.1`:

`New-NetRoute -InterfaceIndex 10 -DestinationPrefix 10.0.0.0/8 -NextHop 192.168.0.1`

You can modify route settings with `Set-NetRoute`, typically to adjust **metric values**.  
Note: You **cannot** modify `DestinationPrefix` or `NextHop` of an existing route using `Set-NetRoute`.

---

### Using the Legacy `route` Command

To view the routing table in Command Prompt:

`route print`

This displays a text-based routing table containing:

- **Network destination** — the target host or network  
- **Netmask** — the subnet mask for the route  
- **Gateway** — the gateway used for IPv4 traffic  
- **Interface** — the IPv4 interface address number  
- **Metric** — the relative cost of the route (lower = preferred)

To add a route using the legacy command (example: add `10.0.0.0/8` via `192.168.0.1` with metric `2`):

`route add 10.0.0.0 mask 255.0.0.0 192.168.0.1 metric 2`

You can remove or change routes using `route delete` or `route change` with the same parameter structure.

---

**Source:**  
https://learn.microsoft.com/en-us/training/modules/troubleshoot-premises-hybrid-networking/5-diagnose-routing-problems

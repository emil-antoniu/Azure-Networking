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

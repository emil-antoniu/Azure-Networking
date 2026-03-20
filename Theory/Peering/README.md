## VNet Peering Overview

### Regional VNet Peering
Connects Azure virtual networks **within the same region**.

### Global VNet Peering
Connects Azure virtual networks **across different regions**.

---

## Gateway Transit

A **VPN gateway** must be configured in the peered virtual network to act as a **gateway transit point**.

Gateway Transit allows the virtual network to communicate with resources **outside the peering**. For example, the subnet gateway could:

- Use a **site‑to‑site VPN** to connect to an on‑premises network.
- Use a **VNet‑to‑VNet** connection to another virtual network.
- Use a **point‑to‑site VPN** to connect to a client.

Source: https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-virtual-networks/7-enable-cross-virtual-network-connectivity-peering
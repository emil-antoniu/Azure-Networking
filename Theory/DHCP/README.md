# DHCP

All network clients must have **unique IP addresses** assigned to their network interfaces.

---

## Troubleshooting the DHCP Server Role

- Ensure the **DHCP server is authorized** in AD DS.
- Verify that the **DHCP Server service** is running.
- Confirm that **available addresses** exist in the DHCP scope for the correct subnet.
- Ensure no devices are using **static IPs** that should have been excluded from the scope.
- Check that any required **DHCP relays** are operational for subnets without a DHCP server.
- Ensure no other services are listening on **UDP ports 67 and 68**.
- Review DHCP **policies and filters**.
- Examine DHCP‑related logs:  
  *Event Viewer → Applications and Services Logs → Microsoft → Windows → DHCP‑Server*
    - DHCP Server debug logs provide details on:
        - IP address lease assignment  
        - DNS dynamic updates  
    - Debug logs are located in:  
      `%windir%\System32\Dhcp`

---

## Troubleshooting the DHCP Client

If a DHCP client cannot contact a DHCP server, it will fall back to an **APIPA address**, limiting communication to the local subnet.

- APIPA prefix: **169.254.0.0/16**

### If the issue appears to be client‑side:

- Verify cabling.
- Ensure the **network adapter** is enabled.
- Update or roll back the **NIC driver** if needed.
- Confirm the **DHCP Client service** is running.
- Ensure no firewall is blocking **UDP ports 67 and 68**.

If **multiple clients** are affected, the issue is more likely with infrastructure (hubs, routers) or the DHCP server itself.

### Client Logs

Check DHCP client logs in:

- *Event Viewer → Applications and Services Logs → Microsoft → Windows → Dhcp‑Client → Operational*
- *Event Viewer → Applications and Services Logs → Microsoft → Windows → Dhcp‑Client → Admin*

---

## IPConfig Commands

Use `ipconfig.exe` to verify and test IP configuration.

| Command              | Description                                      |
|----------------------|--------------------------------------------------|
| `ipconfig /all`      | View detailed configuration information.         |
| `ipconfig /release`  | Release the leased configuration.                |
| `ipconfig /renew`    | Renew the leased configuration.                  |
| `ipconfig /displaydns` | View DNS resolver cache entries.              |
| `ipconfig /flushdns` | Clear the DNS resolver cache.                    |

You can pair IPConfig with a **network analyzer** to capture DHCP traffic.  
Look for datagrams using **UDP ports 67 and 68**, which are used for DHCP communication.

---

**Source:**  
https://learn.microsoft.com/en-us/training/modules/troubleshoot-premises-hybrid-networking/2-diagnose-dhcp-problems

# Azure DNS

Azure public DNS is a hosting service for DNS domains that provides name resolution by using <b>Microsoft Azure infrastructure</b>.

<ul>
<li>The name of the <b>DNS zone</b> must be unique within the resource group, and the zone must not exist already.</li>
<li>The same zone name can be reused in a different <b>resource group</b> or a different <b>Azure subscription</b>.</li>
<li>Where multiple zones share the same name, each instance is assigned different <b>name server addresses</b>.</li>
<li>The <b>root/parent zone</b> is registered at the registrar and pointed to Azure <b>NS name servers</b>.</li>
</ul>

Azure DNS allows you to <b>host a DNS zone</b> and <b>manage DNS records</b> for a domain in Azure.

If you want to set up a separate child zone, you can <b>delegate a subdomain</b> in Azure DNS.

Azure Private DNS manages and resolves domain names in the <b>virtual network</b> without the need to configure a custom DNS solution.
<br><b>Azure Private DNS:</b>

<ul>
<li>Removes the need for creating <b>custom DNS solutions</b>.</li>
<li>Hosts your <b>custom DNS records</b>, including hostname records.</li>
<li>Provides <b>hostname resolution</b> between virtual networks.</li>
<li>Private DNS zones can be <b>shared between virtual networks</b>, simplifying cross‑network and service‑discovery scenarios such as virtual network peering.</li>
<li>Azure DNS private zones are available in <b>all Azure regions</b> in the Azure public cloud.</li>
</ul>

Private DNS zones in Azure are available for <b>internal resources only</b>.

Source: https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-virtual-networks/5-design-name-resolution-virtual-network

## Troubleshooting DNS

If you're experiencing name resolution issues that may relate to the DNS server, consider the following steps.

---

## DNS Server Troubleshooting

- Verify that the **DNS Server service** is running.
- Check the **event logs** for DNS‑related errors.
  - DNS maintains a default **DNS Server log** in Event Viewer:  
    *Applications and Services Logs → Microsoft → Windows → DNS‑Server*
  - This log records:
    - DNS service start/stop events  
    - Background loading and zone signing  
    - DNS configuration changes  
    - Warnings and errors
  - For deeper analysis, enable **debug logging** (disabled by default). Debug options include:
    - Packet direction  
    - Packet contents  
    - Transport protocol  
    - Request type  
    - IP‑based filtering  
    - Log file name and location (`%windir%\System32\DNS`)  
    - Maximum log size
- Determine whether an incorrect DNS response is from an **authoritative server**:
  - If yes, possible causes include:
    - Administrative errors in zone data → review and correct zone records  
    - AD DS replication or dynamic update issues → verify replication health
- If the server is **not authoritative**, the issue may be due to **zone transfer** problems:
  - Check whether the primary zone data is correct  
  - If correct → resync the secondary  
  - If incorrect → fix the primary, then resync

---

## DNS Troubleshooting Tools

### Command‑Line Tools

| Command  | Description |
|----------|-------------|
| **Nslookup** | Query DNS information, validate records, test zone transfers, check MX records, and assess DNS server status. |
| **DNSCmd** | Manage DNS server settings; useful for scripting and automated DNS configuration. |
| **DNSlint** | Diagnose common DNS issues and generate HTML reports on domain status. |
| **IPConfig** | View and modify IP configuration. Includes DNS‑related options: <br>• `ipconfig /displaydns` – View DNS cache <br>• `ipconfig /flushdns` – Clear DNS cache <br>• `ipconfig /registerdns` – Re‑register host records |

---

## PowerShell Cmdlets for DNS

| Cmdlet | Description |
|--------|-------------|
| **Clear-DNSClientCache** | Clears the DNS client cache (similar to `ipconfig /flushdns`). |
| **Get-DNSClient** | Displays network interface details. |
| **Get-DNSClientCache** | Shows the local DNS client cache (similar to `ipconfig /displaydns`). |
| **Register-DNSClient** | Registers all IP addresses of the computer with the DNS server. |
| **Resolve-DNSName** | Performs DNS name resolution (similar to `nslookup`). |
| **Set-DNSClient** | Configures DNS client settings for specific interfaces. |
| **Test-DNSServer** | Tests whether a specified computer is functioning as a DNS server. |

---

**Source:**  
https://learn.microsoft.com/en-us/training/modules/troubleshoot-premises-hybrid-networking/3-diagnose-dns-problems

## Troubleshooting IP Configuration Problems

## Tools for Investigating IP Configuration Problems

### Resource Monitor
A graphical tool for viewing:
- TCP/UDP ports in use  
- Programs using those ports  
- Data transfer activity  

### Network Diagnostics
Windows Network Diagnostics can:
- Identify networking issues  
- Suggest corrective actions  
- Provide descriptions and potential remedies  

### Event Viewer
Event logs record significant system events.  
Useful for identifying:
- IP conflicts  
- Service startup failures  
- Other network‑related errors  

---

## Command‑Line Tools for IP Troubleshooting

| Tool     | Description |
|----------|-------------|
| **IPConfig** | Displays current TCP/IP configuration; refresh DHCP and DNS settings. |
| **Ping** | Tests IP‑level connectivity using ICMP echo requests; may be blocked by firewalls. |
| **Tracert** | Shows the path to a destination and identifies failing routers; results may vary if routers deprioritize ICMP. |
| **Pathping** | Combines Ping and Tracert; provides detailed hop‑by‑hop statistics using 100 packets per hop. |
| **Route** | Views/modifies the local routing table; verify default gateway (0.0.0.0 route). PowerShell equivalents: `Get-NetRoute`, `New-NetRoute`, `Remove-NetRoute`. |
| **Telnet** | Tests whether a server port is listening (e.g., `telnet 10.10.0.10 25`). |
| **Netstat** | Displays network connections and statistics; `netstat -ab` shows listening ports and associated executables. |

---

## Useful PowerShell Cmdlets for Network Troubleshooting

| Cmdlet | Description |
|--------|-------------|
| **Get-NetIPv4Protocol** | Retrieves IPv4 protocol configuration. |
| **Get-NetIPAddress** | Lists IP addresses configured on interfaces. |
| **Get-NetRoute** | Displays routes in the local routing table. |
| **Get-NetConnectionProfile** | Shows network type (public, private, domain). |
| **Test-Connection** | Performs connectivity tests similar to Ping. |
| **Test-NetConnection** | Provides DNS lookup results, interface info, TCP tests, IPsec rules, and connection confirmation. |


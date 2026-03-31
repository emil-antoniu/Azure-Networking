# Packet Monitor

## Capturing and Analyzing Packets with Pktmon.exe

### 1. Choose the packet types to capture
Decide what traffic you want to monitor — by IP address, ports, protocols, and so on.

### 2. Apply capture filters
Use `pktmon filter add <filters>` to define what traffic should be captured.

Example: capture any ICMP traffic to or from `172.16.0.10`, and any traffic on port `53`:

`pktmon filter add -i 172.16.0.10 -t icmp`  
`pktmon filter add -p 53`

### 3. Start the capture and enable logging
`pktmon start -c`

### 4. Reproduce the issue
Perform the action or scenario that triggers the network problem.

### 5. Check counters
Verify that the expected traffic is being captured:

`pktmon counters`

### 6. Stop the capture
`pktmon stop`

### 7. Convert logs to a readable format
Use ETL-to-text conversion:

`pktmon etl2txt <filename>`

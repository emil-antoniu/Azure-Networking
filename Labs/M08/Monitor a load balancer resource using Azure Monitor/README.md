# Monitor a load balancer resource using Azure Monitor

## Overview

Create an internal load balancer and observe various monitoring tools in action.

![Topology](./images/topology.png)

### Task 1: Create the virtual network

![VNet created](./images/vnet-created.png)

### Task 2: Create the load balancer

![Load balancer created](./images/load-balancer-created.png)

### Task 3: Create a backend pool

![Backend pool created](./images/backend-pool-created.png)

### Task 4: Create a health probe

![Health probe created](./images/health-probe-created.png)

### Task 5: Create a load balancer rule

![Load balancer rule created](./images/load-balancer-rule-created.png)

### Task 6: Create backend servers

Changes made to `azuredeploy.json`:
```json
"defaultValue": "Standard_D2s_v3" -> "defaultValue": "Standard_DC1s_v3"
"sku": "2019-Datacenter" -> "sku": "2019-datacenter-gensecond" // For both VMs
```

Changes made to `azuredeploy.parameters.json`:
```json
"value": "Standard_D2s_v3" -> "value": "Standard_DC1s_v3"
```

```PowerShell
$RGName = "IntLB-RG"

New-AzResourceGroupDeployment -ResourceGroupName $RGName -TemplateFile azuredeploy.json -TemplateParameterFile azuredeploy.parameters.json
```

![VMs created](./images/vms-created.png)

### Task 7: Add VMs to the backend pool

![Add VMs to backend pool](./images/vms-to-backend-pool.png)

### Task 8: Test the load balancer

It did show myVM1 once.

![Test 2](./images/test-2.png)

### Task 9: Create a Log Analytics Workspace

![LAW created](./images/LAW-created.png)

### Task 10: Use Functional Dependency View

![Insights](./images/insights.png)

The Metrics pane provides a quick view of some key metrics for this load balancer resource, in the form of bar and line charts (or it would have had I not been a free tier in 2026).

![Metrics erroring out](./images/FDV-error.png)

### Task 11: View detailed metrics

- **Overview**: shows the availability status of the load balancer and overall Data Throughput and Frontend and Backend Availability for each of the Frontend IPs attached to your Load Balancer. These metrics indicate whether the Frontend IP is responsive and the compute instances in your Backend Pool are individually responsive to inbound connections.

- **Frontend & Backend Availability**: Health Probe Status charts. If you see values that are lower than 100 for these items, it indicates an outage of some kind on those resources.

- **Data Throughpu**t: you will see that the values change to show the exact value at any point in time.

- **Flow Distribution**: graphical representation of the aforementioned.

![Detailed metrics](./images/free-tier-struggle.png)

### Task 12: View resource health

![Resource health](./images/resource-health.png)

### Task 13: Configure diagnostic settings

![Diagnostic settings](./images/diagnostic-settings.png)

### Scripting

Clean-up after lab.

```PowerShell
Remove-AzResourceGroup -Name 'IntLB-RG' -Force -AsJob
```

Source: https://microsoftlearning.github.io/AZ-700-Designing-and-Implementing-Microsoft-Azure-Networking-Solutions/Instructions/Exercises/M08-Unit%203%20Monitor%20a%20load%20balancer%20resource%20using%20Azure%20Monitor.html
# Configure DNS settings in Azure

## Overview

## Key Activities

### Task 1: Create a private DNS Zone

![DNS Zone created](./images/dns-zone-created.png)

### Task 2: Link subnet for auto registration

![VNet link created](./images/vnet-link-created.png)

### Task 3: Create Virtual Machines to test the configuration

New-AzResourceGroupDeployment: 12:35:03 PM - Error: Code=InvalidTemplateDeployment; Message=The template deployment 'azuredeploy' is not valid according to the validation procedure. The tracking id is '557ea084-c2e6-4b8c-b504-35e2bad7051f'. See inner errors for details.
New-AzResourceGroupDeployment: 12:35:03 PM - Error: Code=SkuNotAvailable; Message=The requested VM size for resource 'Following SKUs have failed for Capacity Restrictions: Standard_D2s_v3' is currently not available in location 'eastus'. Please try another size or deploy to a different location or different zone. See https://aka.ms/azureskunotavailable for details.
New-AzResourceGroupDeployment: The deployment validation failed

### Scripting

Source: https://microsoftlearning.github.io/AZ-700-Designing-and-Implementing-Microsoft-Azure-Networking-Solutions/Instructions/Exercises/M01-Unit%206%20Configure%20DNS%20settings%20in%20Azure.html
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
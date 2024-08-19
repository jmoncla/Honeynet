# Building a SOC + Honeynet in Azure (Live Traffic)
![Cloud Honeynet / SOC](https://i.imgur.com/ZWxe03e.jpg)

For this lab, I set up a SOC + Honeynet using Microsoft Azure. I was able to create virtual machines, expose them to the internet, generate logs and incidents, and practice remediating the incidents through hardening of the environment. <br><br>
The following tools and architecture were used to complete this project:

- Microsoft Azure 
- Virtual Network (VNet)
- Windows and Linux Virtual Machines
- Network Security Groups (NSGs)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel
- Local SQL Database
- Microsoft Defender for Cloud (MDC)
- NIST SP 800-53
- Windows Event Viewer
- Kusto Query Language (KQL)
- PowerShell
  
<br>
Project Summary<br> <br> 
1. Virtual machines were created using Microsoft Azure.<br>
2. The virtual machines were configured to forward logs to Log Analytics workspace within Azure.<br>
3. The virtual machines were made vulnerable and exposed to the internet after disabling the network security groups within Azure and disabling the built-in firewalls native to the VMs.<br>
4. Logs were generated as malicious actors made authorization attempts on the virtual machines.<br><br> 
This is an example of the location and scale of the attacks on the VMs by malicious actors using data from the environment I created. Using Microsoft Sentinel Workbooks you can visualize the attackers' location on a global level. <br><br>
<img src="https://github.com/jmoncla/Honeynet/blob/main/geomaplab.PNG" alt="Geomap Lab Screenshot" width="1000" /><br> <br> 


5. The logs were then passed along to Log Analytics and made available for queries.<br>
6. Custom rules were created in Sentinel to generate incidents for:<br><br> 
- Security Events (Windows VMs)<br> 
- Syslog (Linux VMs)<br> 
- SecurityAlert (Microsoft Defender for Cloud)<br> 
- SecurityIncident (Sentinel Incidents)<br> 
- NSG Inbound Malicious Flows Allowed<br><br>
7. With the Virtual Machines fully exposed to the internet data was collected for 24 hours.<br>
8. After 24 hours the environment was hardened according to NIST 800-53 using Microsoft Defender for Cloud's guidance/recommendations for hardening.<br>
9. Finally, after, hardening, data was collected for another 24 hours to examine the effects of the increased security.<br><br>

Here are the results before and after implementing the security solutions: <br><br>

## Before Hardening

| Security Events                          | Count  |
|------------------------------------------|--------|
| Security Events (Windows VMs)            | 93288  |
| Syslog (Linux VMs)                        | 30094  |
| SecurityAlert (Microsoft Defender for Cloud) | 6     |
| SecurityIncident (Sentinel Incidents)     | 335    |
| NSG Inbound Malicious Flows Allowed       | 1419   |

## After Hardening

| Security Events                          | Count  |
|------------------------------------------|--------|
| Security Events (Windows VMs)            | 17079  |
| Syslog (Linux VMs)                        | 2769   |
| SecurityAlert (Microsoft Defender for Cloud) | 0    |
| SecurityIncident (Sentinel Incidents)     | 0      |
| NSG Inbound Malicious Flows Allowed       | 0      |

## Change After Security Environment Update

| Security Events                          | Change (%)       |
|------------------------------------------|------------------|
| Security Events (Windows VMs)            | -81.69%          |
| Syslog (Linux VMs)                        | -90.80%          |
| SecurityAlert (Microsoft Defender for Cloud) | -100.00%      |
| Security Incident (Sentinel Incidents)    | -100.00%         |
| NSG Inbound Malicious Flows Allowed       | -100.00%         |

 So, we can see the hardening was successful as the number of security events and incidents was drastically reduced after the security controls were applied.
 


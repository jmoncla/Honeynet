# Building a SOC + Honeynet in Azure (Live Traffic)
![Cloud Honeynet / SOC](https://i.imgur.com/ZWxe03e.jpg)

For this lab, I set up a SOC + Honeynet with the following architecture:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel
- Local SQL Database
<br>
1. Virtual machines were created using Microsoft Azure.<br>
2. The virtual machines were configured to forward logs to Log Analytics workspace within Azure.<br>
3. The virtual machines were made vulnerable and exposed to the internet after disabling the network security groups within Azure and disabling the built-in firewalls native to the VMs themselves.<br>
4. Logs were generated as malicious actors made authorization attempts on the virtual machines.<br>
5. The logs were passed along to Log Analytics and made available for queries.<br>
6. The authorization attempts were then selected and made into their respective workbooks for visualization using Microsoft Sentinel.<br>
7. The workbooks are configured to map the attacker's location based on their IP address.<br><br>

These are Windows Remote Desktop Failed Authentication logins from across the globe. This data is from the logs of the windows VM I set up and the visualization is through Sentinel Workbooks.<br><br>
<img src="https://github.com/jmoncla/Honeynet/blob/main/geomaplab.PNG" alt="Geomap Lab Screenshot" width="1000" />

The next step of the project will be to harden Network Security Groups by blocking ALL traffic with the exception of my admin workstation as well as hardening all other resources which will be configured to be protected by their built-in firewalls.<br>
I will be able to analyze the metrics before and after hardening and they will be reported in this project later on. 


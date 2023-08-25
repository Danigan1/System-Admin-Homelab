# Emulating a Security Operations Center (SOC) with an Azure Honeynet: Live Attacker Traffic!

![68747470733a2f2f692e696d6775722e636f6d2f5a5778653033652e6a7067](https://user-images.githubusercontent.com/109401839/236074219-a957c5f2-21e9-4501-9d9d-ed879e01558f.jpg)

## Introduction

In this project, I create a compact honeynet model in Microsoft Azure, drawing in real-world attacker traffic from global sources. The overarching aim is to showcase optimal security practices, effective incident response strategies, and the effects of hardening your environment. This objective is pursued by deliberately setting up virtual machines, intentionally lacking safeguards against public internet access, to entice potential attackers into our controlled environment. After aggregating various log sources into the Log Analytics Workspace, the deployment of Microsoft Sentinel becomes instrumental. This tool generates attack visualizations, triggers alerts, and compiles incident reports. 
Furthermore, the project includes a comparative analysis of metrics, both prior to and post the application of security strengthening measures. These insights are drawn from the incidents observed during the 24-hour monitoring period, offering a comprehensive view of the improvements achieved.


# Azure Services Employed

- Azure Virtual Network (VNet)
- Azure Network Security Group (NSG)
- Virtual Machines (2x Windows, 1x Linux)
- Log Analytics Workspace with Kusto Query Language (KQL) Queries
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel
- Microsoft Defender for Cloud


## Architecture Before Hardening / Security Controls

![Architecture Diagram](https://i.imgur.com/aBDwnKb.jpg)

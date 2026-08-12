# Tines SOAR Integration with Wazuh & Automated Security Response

## 🎯 Objective:
Integrate Wazuh with Tines SOAR to automate security alert processing, threat intelligence enrichment, analyst notification, and controlled response actions. The objective was to build an end-to-end workflow that detects suspicious activity, enriches indicators, obtains analyst approval, and triggers Wazuh Active Response.

## 📊 Project Overview:
This project focused on extending Wazuh's security monitoring capabilities through Tines SOAR. Since native Tines integration was not available, a custom Wazuh integration was configured using a custom integration script and webhook. Wazuh alerts were forwarded to Tines, enriched using AbuseIPDB and VirusTotal, and communicated through Slack. An analyst approval workflow was then implemented to allow or deny automated IP blocking through the Wazuh API.

## 🧰 Tools Used:
- Wazuh SIEM
- Tines SOAR
- Wazuh API
- Wazuh Active Response
- AbuseIPDB
- VirusTotal
- Slack
- ngrok
- Windows 10
- Ubuntu Linux
- SSH
- Python
- Wazuh Custom Integration
- Wazuh Custom Rules

## 🛡️ Skill Developed:
- SOAR workflow design and orchestration
- Security alert triage and enrichment
- AI-assisted security analysis
- Human-in-the-loop response design
- Threat intelligence investigation
- API-based security automation
- Webhook-based integration
- Incident response automation
- Security decision-making and validation
- Detection-to-response workflow development

## 📁 Key Deliverables:
- Custom Tines-Wazuh integration
- Wazuh-Tines webhook configuration
- Tines SOC automation workflow
- AbuseIPDB and VirusTotal enrichment workflow
- Slack notification workflow
- AI Task Agent with structured IOC analysis
- Analyst approval page with block/allow decision
- Tines-Wazuh API connectivity
- Automated Wazuh Active Response workflow
- End-to-end IP blocking demonstration

## 🔍 Steps Performed:

### 1. Configured Custom Wazuh Integration
- Verified that the deployed Wazuh version did not provide native Tines integration.
- Created a custom integration based on the existing Wazuh integration structure by:
  - Copying the shuffle integration.
  - Renaming it to custom-tines.
  - Renaming the associated Python script to custom-tines.py.
  - Updating ownership to the 'wazuh' group.
  - Configuring the integration to communicate with Tines through a webhook.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/171e9a69-b27a-4272-a815-d92baf71ed52" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/b8f3ee64-9c40-42cd-97a3-7eb592a456fa" />
<img width="785" height="230" alt="image" src="https://github.com/user-attachments/assets/f3d20709-7591-4d9a-88a8-454e3b2342a5" />

### 2. Created Tines Webhook & Workflow
- Configured Tines by:
  - Creating a Tines Stories tenant.
  - Creating a dedicated team named 'Wazuh-SOC-Analyst-Challenge’ '
  - Creating the Wazuh-Webhook.
  - Copying the webhook URL.
  - Configuring Wazuh to forward matching security events to Tines in JSON format.
- Configured the Wazuh Manager to forward events matching the custom SSH brute-force detection rule.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/663a29c6-d76c-4e0e-ba9e-7d6370a9939b" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/fb50b9ee-3b18-4fd7-a8ab-947b54cd83a3" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/cae127d1-c6f9-4d55-91f2-de7e22a5f301" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/dd8a566b-409d-4507-94e3-859178d38933" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/ac0afe6a-2b7c-4d1d-adf5-de8e4eb20b26" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/dfa52a1d-114b-4a5a-b8ff-50a695f75318" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/5a7bb697-697e-40b2-9664-3fcc01e9af90" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/809f88b8-0925-4606-a362-43133994250b" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/816731d6-7c84-47b9-8ec6-206c1b788533" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/81c4ab7b-59ea-4c9e-8bf3-0b09125e8fc9" />

### 3. Validated Wazuh Alert Ingestion
- Generated three failed SSH authentication attempts from the Windows endpoint against the Linux server.
- The activity triggered the Wazuh custom rule: **'Multiple SSH login failures observed from the same source IP'**.
- The resulting Wazuh alert was successfully received by the Tines webhook and appeared within the Tines Story.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/ecb7c307-ce03-44ff-b163-b94617868b3e" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/fdf9397b-6904-493d-9efd-f73b4f2319d3" />

### 4. Built AI-Assisted Threat Intelligence Enrichment
- Added a Tines AI Task Agent to analyze incoming Wazuh alerts and enrich indicators using:
  - AbuseIPDB – IP reputation
  - VirusTotal – IPs, URLs, domains, files and comments
  - Slack – SOC notification and communication
- Configured the required API credentials and updated the AI Agent system instructions and prompt.

📌 Refer to the below screenshots: (left to right)

<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/157d98e7-dbf6-4ecb-b2f4-9aabe32c4af6" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/ea880452-f177-4c2e-a83d-eaa98c8d54af" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/c03214a1-6c9d-432b-97e0-a783689867ce" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/e701eeea-f906-4ca9-baf8-d96ce3971713" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/a75a0f4b-31c6-4030-b5a8-79744d09c9f6" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/08c25c70-f897-4efa-858b-b6730543cf95" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/41ea99fd-c420-48c4-a0d7-44cea60aea92" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/3456c0db-835f-471a-b9d1-3df97745735f" />
<img width="975" height="521" alt="image" src="https://github.com/user-attachments/assets/d9d2f00a-f45a-43e6-8d76-0e0657b63e69" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/62718836-a579-40f0-a51b-9b0d604add58" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/7c91f402-9018-4f42-b3b8-3b6dee59942d" />
<img width="975" height="582" alt="image" src="https://github.com/user-attachments/assets/aadcc2c8-c72d-4a66-bcc6-b2d5ed97ef53" />
<img width="975" height="582" alt="image" src="https://github.com/user-attachments/assets/4873cb48-f5e5-4cd9-b6c6-60d058dae7dc" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/f598ac8c-17b6-4b6d-a2a6-35100121e957" />
<img width="975" height="532" alt="image" src="https://github.com/user-attachments/assets/d15cfedc-c6a1-4970-8480-acfb479d7785" />
<img width="975" height="536" alt="image" src="https://github.com/user-attachments/assets/d0910dc5-3258-48bc-bba7-bc261a609bcf" />
<img width="975" height="580" alt="image" src="https://github.com/user-attachments/assets/1093fdb6-44b5-4dce-8da6-46cf4d5c93dd" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/2a203a65-eab3-48d4-9f2e-598d66dae0e1" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/e7cf3ab3-3a1d-4fab-aa2f-b21a2dea9209" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/60435a7f-5975-44ce-a66d-ba925425ec75" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/72bceecb-283f-47d6-8a35-0e5aef4a53a1" />
<img width="975" height="564" alt="image" src="https://github.com/user-attachments/assets/6682c807-f6b5-418d-91b1-ee99703712d9" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/0f82b48e-a592-40b4-b8e9-7593da5592ae" />
<img width="975" height="565" alt="image" src="https://github.com/user-attachments/assets/4fdce8d3-92f1-45a8-a538-1e9d1e735f00" />
<img width="975" height="564" alt="image" src="https://github.com/user-attachments/assets/a596bb45-6ee5-48dd-a6a8-a65964e3559b" />
<img width="975" height="563" alt="image" src="https://github.com/user-attachments/assets/1fe206f4-06da-474d-815e-cac8ac16926c" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/639f7f38-7897-420c-bc51-02e6204c093f" />

### 5. Implemented Slack SOC Notifications
- Configured Slack integration within Tines and tested the connection using the appropriate channel ID.
- Replayed a Wazuh event through the webhook and verified that Tines generated a Slack notification containing the relevant alert and enrichment information.

📌 Refer to the below screenshots: (left to right)



6. Created Analyst Approval Workflow

Extended the workflow to determine whether an IP should be blocked.

The AI Agent was configured to provide structured output containing:

recommend_block
ioc_type
ioc_value

Tines Event Transform actions were then used to extract these values from the AI output.

Created conditional branches for:

Block is recommended
Don't block

📸 Screenshot – Tines Conditional Workflow

[INSERT SCREENSHOT HERE]

7. Built Analyst Decision Page

Created a Tines page to obtain analyst approval before executing the blocking action.

The page included interactive controls allowing the analyst to choose whether the identified IP should be blocked.

This introduced a human-in-the-loop approval step before automated containment.

📸 Screenshot – Analyst Approval Page

[INSERT SCREENSHOT HERE]

8. Tested the SOAR Workflow with a Simulated Alert

Generated a mock Wazuh security event containing suspicious process execution, PowerShell activity, MITRE ATT&CK techniques, and a destination IP.

Sent the event directly to the Tines webhook to validate the workflow independently of a live detection.

Verified that the event successfully passed through the workflow and generated the expected enrichment and response logic.

📸 Screenshot – Mock Wazuh Event

[INSERT SCREENSHOT HERE]

📸 Screenshot – Tines Workflow Execution

[INSERT SCREENSHOT HERE]

9. Integrated Tines with the Wazuh API

Retrieved the Wazuh API credentials from the Wazuh Manager.

Because the Wazuh Manager was hosted on-premises, configured ngrok to provide secure external access to the Wazuh API.

Configured:

Wazuh API endpoint
Authentication credentials
SSL verification settings
API authentication token extraction

Successfully tested the Wazuh API connection from Tines.

📸 Screenshot – ngrok Configuration

[INSERT SCREENSHOT HERE]

📸 Screenshot – Wazuh API Credentials in Tines

[INSERT SCREENSHOT HERE]

📸 Screenshot – Successful Wazuh API Authentication

[INSERT SCREENSHOT HERE]

10. Connected Tines to Wazuh Active Response

Configured the Tines Run Command in Wazuh functionality to communicate with the Wazuh API.

Updated the AI Agent and Slack notification components to support the automated response workflow.

The workflow was designed to execute Wazuh Active Response only after the appropriate condition and analyst approval were satisfied.

📸 Screenshot – Tines Wazuh Active Response Configuration

[INSERT SCREENSHOT HERE]

11. Validated End-to-End Automated Response

Generated another SSH brute-force scenario from the Windows endpoint against the Linux server.

The workflow successfully performed:

SSH Brute Force → Wazuh Detection → Tines Webhook → AI Analysis → Threat Intelligence Enrichment → Analyst Approval → Wazuh API → Active Response → IP Blocking

After selecting Yes to block the malicious IP, Tines triggered Wazuh Active Response and the source IP was successfully blocked at the firewall.

📸 Screenshot – Brute Force Detection

[INSERT SCREENSHOT HERE]

📸 Screenshot – Tines Analyst Approval

[INSERT SCREENSHOT HERE]

📸 Screenshot – Active Response Execution

[INSERT SCREENSHOT HERE]

📸 Screenshot – IP Blocked at Firewall

[INSERT SCREENSHOT HERE]

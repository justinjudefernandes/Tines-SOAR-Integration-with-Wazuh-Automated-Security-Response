# Tines SOAR Integration with Wazuh & Automated Security Response

## 🎯 Objective:
Integrate Wazuh with Tines SOAR to automate security alert processing, threat intelligence enrichment, analyst notification, and controlled response actions. The objective was to build an end-to-end workflow that detects suspicious activity, enriches indicators, obtains analyst approval, and triggers Wazuh Active Response.

## 📊 Project Overview:
This project focused on extending Wazuh's security monitoring capabilities through Tines SOAR. Since native Tines integration was not available, a custom Wazuh integration was configured using a custom integration script and webhook. Wazuh alerts were forwarded to Tines, enriched using AbuseIPDB and VirusTotal, and communicated through Slack. An analyst approval workflow was then implemented to allow or deny automated IP blocking through the Wazuh API.

🧰 Tools Used:
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

🛡️ Skill Developed:
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

📁 Key Deliverables:
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

🔍 Steps Performed:
1. Configured Custom Wazuh Integration

Verified that the deployed Wazuh version did not provide native Tines integration.

Created a custom integration based on the existing Wazuh integration structure by:

Copying the shuffle integration.
Renaming it to custom-tines.
Renaming the associated Python script to custom-tines.py.
Updating ownership to the wazuh group.
Configuring the integration to communicate with Tines through a webhook.

📸 Screenshot – Wazuh Custom Integration

[INSERT SCREENSHOT HERE]

2. Created Tines Webhook & Workflow

Configured Tines by:

Creating a Tines Stories tenant.
Creating a dedicated SOC team.
Creating the Wazuh-Webhook.
Copying the webhook URL.
Configuring Wazuh to forward matching security events to Tines in JSON format.

Configured the Wazuh Manager to forward events matching the custom SSH brute-force detection rule.

📸 Screenshot – Tines Wazuh Webhook

[INSERT SCREENSHOT HERE]

📸 Screenshot – Wazuh Webhook Configuration

[INSERT SCREENSHOT HERE]

3. Validated Wazuh Alert Ingestion

Generated three failed SSH authentication attempts from the Windows endpoint against the Linux server.

The activity triggered the Wazuh custom rule:

Multiple SSH login failures observed from the same source IP

The resulting Wazuh alert was successfully received by the Tines webhook and appeared within the Tines Story.

📸 Screenshot – Wazuh Alert in Tines

[INSERT SCREENSHOT HERE]

4. Built AI-Assisted Threat Intelligence Enrichment

Added a Tines AI Task Agent to analyze incoming Wazuh alerts and enrich indicators using:

AbuseIPDB – IP reputation
VirusTotal – IPs, URLs, domains, files and comments
Slack – SOC notification and communication

Configured the required API credentials and updated the AI Agent system instructions and prompt.

📸 Screenshot – Tines AI Task Agent

[INSERT SCREENSHOT HERE]

📸 Screenshot – AbuseIPDB / VirusTotal Configuration

[INSERT SCREENSHOT HERE]

5. Implemented Slack SOC Notifications

Configured Slack integration within Tines and tested the connection using the appropriate channel ID.

Replayed a Wazuh event through the webhook and verified that Tines generated a Slack notification containing the relevant alert and enrichment information.

📸 Screenshot – Tines Slack Configuration

[INSERT SCREENSHOT HERE]

📸 Screenshot – Wazuh Alert Notification in Slack

[INSERT SCREENSHOT HERE]

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

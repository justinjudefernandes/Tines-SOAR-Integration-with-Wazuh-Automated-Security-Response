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
  - Creating a dedicated team named 'Wazuh-SOC-Analyst-Challenge’.
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
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/41798bf7-1de0-4442-8cb6-b05a9d999f86" />
<img width="975" height="563" alt="image" src="https://github.com/user-attachments/assets/225ea344-ecb5-4c47-bd81-a6211a4b32ce" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/b443a9a5-b1da-449c-acb2-d0d35f403f52" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/e18ac7ec-666c-487c-861d-7e0972485cf9" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/761f1a40-1c83-4daa-8d18-6e64ff736e5d" />


### 5. Implemented Slack SOC Notifications
- Configured Slack integration within Tines and tested the connection using the appropriate channel ID.
- Replayed a Wazuh event through the webhook and verified that Tines generated a Slack notification containing the relevant alert and enrichment information.

📌 Refer to the below screenshots: (left to right)

<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/8cf7c9d1-2460-40f0-bc2d-f552c0270767" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/ef6eccba-67b0-42c5-b4f0-9be5b0b540a5" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/8a270815-f1fc-4c7c-aed2-d64667ace7b4" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/689cd762-3ab5-4ff4-a2b1-ff45cf209f33" />
<img width="975" height="556" alt="image" src="https://github.com/user-attachments/assets/2a848660-e08f-4a1e-ad60-56c3962fef34" />

### 6. Created Analyst Approval Workflow
- Extended the workflow to determine whether an IP should be blocked.
- The AI Agent was configured to provide structured output containing:
  - recommend_block
  - ioc_type
  - ioc_value
- Tines Event Transform actions were then used to extract these values from the AI output.
- Created conditional branches for:
  - Block is recommended
  - Don't block

📌 Refer to the below screenshots: (left to right)

<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/688ca3f7-cf73-4e2a-ad67-0be2dc6f1793" />
<img width="975" height="551" alt="image" src="https://github.com/user-attachments/assets/4c8bf7b2-8c52-4b15-897e-3fada8e9971d" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/a9387d10-9341-4b99-a445-4714aa2e3e1a" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/af29ca03-16e8-4072-8b42-92ec118f7d87" />
<img width="975" height="564" alt="image" src="https://github.com/user-attachments/assets/7969d7f4-6f19-4e68-9459-dce9124f6602" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/277b28b1-0638-4ea9-abdb-cb2976465d18" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/bf383213-43ee-40fd-bbd7-11bdd74f6673" />

### 7. Built Analyst Decision Page
- Created a Tines page to obtain analyst approval before executing the blocking action.
- The page included interactive controls allowing the analyst to choose whether the identified IP should be blocked.
- This introduced a human-in-the-loop approval step before automated containment.

📌 Refer to the below screenshots: (left to right)

<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/1611b1ed-1140-4d2e-8ef5-71a9a1be3eb6" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/24b0397a-0d8b-42d0-b33b-3588c9391388" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/faba5896-05bf-445c-8177-81e8e5daaf5c" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/9066c6bf-b1ab-45e8-a9c1-8f6873fbd28c" />

### 8. Tested the SOAR Workflow with a Simulated Alert
- Generated a mock Wazuh security event containing suspicious process execution, PowerShell activity, MITRE ATT&CK techniques, and a destination IP.
- Sent the event directly to the Tines webhook to validate the workflow independently of a live detection.
- Setup up the Active response workflow by creating a condition named ‘Yes to Block’.
- Verified that the event successfully passed through the workflow and generated the expected enrichment and response logic.

📌 Refer to the below screenshots: (left to right)

<img width="975" height="582" alt="image" src="https://github.com/user-attachments/assets/536e2e02-f9cb-4a59-aeb5-1d5f1d3f4fe4" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/884656e4-01ce-489f-a74e-4826caacd24c" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/d1e2c8c8-6747-471c-ba4b-4c876cb94613" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/7e4be330-a302-4b6a-875c-216db2cf024c" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/25dfb9b7-d5cd-4fe0-a27b-a547a7d0e2d7" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/4abf7df7-9c56-44b5-a9ef-26f278c31761" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/4fe43c4c-11d0-4a3e-a50d-67201370acb3" />

### 9. Integrated Tines with the Wazuh API
- Retrieved the Wazuh API credentials from the Wazuh Manager.
- Because the Wazuh Manager was hosted on-premises, configured ngrok to provide secure external access to the Wazuh API.
- Configured:
  - Wazuh API endpoint
  - Authentication credentials
  - SSL verification settings
  - API authentication token extraction
- Successfully tested the Wazuh API connection from Tines.

📌 Refer to the below screenshots: (left to right)

<img width="975" height="582" alt="image" src="https://github.com/user-attachments/assets/c425376a-b9fa-4130-a326-7a7ffb10a6b0" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/10ac0f6b-1cef-4db2-babe-68dab6f61715" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/77ef0b0a-6aec-4670-bb72-322517d92b70" />
<img width="975" height="556" alt="image" src="https://github.com/user-attachments/assets/f35f4457-b332-4d0e-a5e6-a525ef5050af" />
<img width="975" height="578" alt="image" src="https://github.com/user-attachments/assets/4abb0919-23d3-4315-a21d-a93dedd0494b" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/57ca6906-9ba7-4e74-b47b-39e3c6d85bdc" />
<img width="975" height="582" alt="image" src="https://github.com/user-attachments/assets/b0c54ced-96d1-4176-89a2-d92f2f2f325c" />
<img width="975" height="579" alt="image" src="https://github.com/user-attachments/assets/0cf7181d-41e5-4935-abf5-a9f23d020749" />
<img width="975" height="583" alt="image" src="https://github.com/user-attachments/assets/14f83eb7-91e5-4dda-99c4-3f54f5bed832" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/7dec8a1a-34ae-467a-a634-24dcd3c17fc5" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/cbed33fd-f10e-40d4-bcc0-4e782d30a6d2" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/e8aa7a0d-d58c-4145-aa3e-78a7699fad45" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/54a38a78-dddc-4c81-b94c-d41f7b753604" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/df7a7128-d79a-4f69-9a24-9273a83eb1ef" />
<img width="975" height="556" alt="image" src="https://github.com/user-attachments/assets/547cd1b2-972f-4199-a9ed-9f464c8db1f8" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/618954f4-5cfd-4ac1-9c09-b872a0ffba12" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/8fc8b128-9a13-4678-a544-a910174db77f" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/4c0405f0-beca-436b-a4b9-a27681f53444" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/06628358-67e3-4f77-8774-d35caa457795" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/c87e2181-3dd6-4efe-9ce7-c568c0242ef6" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/4f58184b-57ca-4d13-9d98-a662db2340bb" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/d9af06f8-5c98-4a14-a5d2-b6f42f367a03" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/2a26a5ef-7a27-44e4-bdd4-2720df9dd08c" />

### 10. Connected Tines to Wazuh Active Response
- Configured the Tines Run Command in Wazuh functionality to communicate with the Wazuh API.
- Updated the AI Agent and Slack notification components to support the automated response workflow.
- The workflow was designed to execute Wazuh Active Response only after the appropriate condition and analyst approval were satisfied.

📌 Refer to the below screenshots: (left to right)

<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/271431ae-b16c-4f4f-91f6-e5b41e881962" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/05fe4bfd-36e4-4a6e-ba31-b5eb8c1f9968" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/8f9ac921-761e-4407-9c0d-c3f52f52a594" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/14836560-4274-4772-924b-18924701b5fd" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/5802d4d4-8ab0-4aa1-bade-d0a68dc269ae" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/2471f568-942e-4ce5-b807-582c377ce30d" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/bb3dbfcc-a9ec-4d8f-882d-cf685397fd22" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/9824d94b-a0e1-4e98-b36f-472be8518277" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/fb9ccd0b-e8e8-48aa-bc33-738419af79b0" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/f6335454-a3bc-4491-990e-8efa3b662c06" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/e83d3fe9-75a2-40a0-b554-f19f2f868500" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/a453a1a2-8c90-4adf-8825-155610f7f334" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/c8e295f3-2346-41be-a871-8c95d534f185" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/8ff1ae9b-f224-4723-a107-6bc42163149b" />

### 11. Validated End-to-End Automated Response
- Generated another SSH brute-force scenario from the Windows endpoint against the Linux server.
- The workflow successfully performed:
  - SSH Brute Force → Wazuh Detection → Tines Webhook → AI Analysis → Threat Intelligence Enrichment → Analyst Approval → Wazuh API → Active Response → IP Blocking
- After selecting Yes to block the malicious IP, Tines triggered Wazuh Active Response and the source IP was successfully blocked at the firewall.

📌 Refer to the below screenshots: (left to right)
<img width="975" height="572" alt="image" src="https://github.com/user-attachments/assets/cd7c178c-9053-4c64-bfd0-91e61b479ef4" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/98056f58-4ea5-454f-95f5-4daf0ead605d" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/0eab46d6-e0f0-4fe5-96cf-7c14b1c8b27c" />
<img width="975" height="579" alt="image" src="https://github.com/user-attachments/assets/de83058d-c66b-4185-95f3-7ddf6afe5cac" />



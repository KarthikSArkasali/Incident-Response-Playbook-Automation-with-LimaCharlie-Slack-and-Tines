# Automated Incident Response Playbook with SOAR & EDR Integration

**Overview:**  
Design and implement a fully automated incident response playbook leveraging LimaCharlie EDR and Tines SOAR, with Slack and email integration for real‑time decision workflows and rapid endpoint isolation.

## 🏗️ Step 1: Architecture & Workflow  
![Playbook Logic Diagram](images/edr-playbook-diagram.png)  
Created end‑to‑end block diagram in Draw.io illustrating detection → decision → response flow.


## 💻 Step 2: EDR Deployment  
| Component            | Host                  | Role                      |
|----------------------|-----------------------|---------------------------|
| LimaCharlie Agent    | Windows Server 2022   | EDR telemetry & controls  |
| Verification         | `sc query limacharlie`| Ensured agent heartbeat   |


## 🔍 Step 3: Telemetry & Detection Rules  
1. **Rule Creation**  
   - Developed custom Detection & Response rules in LimaCharlie  
2. **Telemetry Generation**  
   - Installed and executed **LaZagne** on Windows Server  
   - Validated LaZagne events in the LimaCharlie console  

## 🔄 Step 4: SOAR & Collaboration Integration  
1. **Tines SOAR**  
   - Ingested LimaCharlie alerts into Tines  
   - Orchestrated multi‑channel actions (Slack, Gmail)  
2. **Communication Channels**  
   - Configured Slack workspace notifications  
   - Integrated Gmail for email alerts  

## 🎛️ Step 5: Playbook Automation & Decisioning  
| Trigger         | Human Prompt     | Action: “Yes”                      | Action: “No”                            |
|-----------------|------------------|------------------------------------|-----------------------------------------|
| LaZagne event   | “Isolate endpoint?” | 1. Isolate host via LimaCharlie<br>2. Slack: “Endpoint isolated” | 1. No isolation<br>2. Slack: “Investigate host” |

## 🔑 Key Highlights  
- **Seamless EDR + SOAR**: LimaCharlie detection feeds Tines playbook  
- **User‑Driven Workflows**: Prompts in Slack drive containment decisions  
- **Rapid Isolation**: Automated endpoint quarantine via EDR API  
- **Multi‑Channel Alerts**: Slack & email ensure visibility  

## 📁 Repo Structure  

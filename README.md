# Automated Incident Response Playbook with SOAR & EDR Integration

## Objective:
This project focuses on designing and implementing an automated incident response playbook using LimaCharlie for advanced detection and response. The system integrates seamlessly with Slack, email, and Tines to deliver powerful Security Orchestration, Automation, and Response (SOAR) capabilities. The playbook incorporates user-driven decision workflows, enabling rapid isolation of compromised endpoints based on real-time security event analysis.

## 🏗️ Step 1: Architecture & Workflow  

![EDR Project Block Dgm](https://github.com/user-attachments/assets/9293ea77-5f12-47a9-9ef3-ccce0614c48e)

Created end‑to‑end block diagram in Draw.io illustrating detection → decision → response flow.


## 💻 Step 2: EDR Deployment  
| Component            | Host                  | Role                      |
|----------------------|-----------------------|---------------------------|
| LimaCharlie Agent    | Windows Server 2022   | EDR telemetry & controls  |
| Verification         | `sc query limacharlie`| Ensured agent heartbeat   |

![Services](https://github.com/user-attachments/assets/cbf8d524-5cea-4832-8468-d8837b1edc18)

## 🔍 Step 3: Telemetry & Detection Rules  
1. **Rule Creation**  
   - Developed custom Detection & Response rules in LimaCharlie
     
![Created Rule](https://github.com/user-attachments/assets/c98e8c38-16ac-45a9-8384-2549c319f6b6)

2. **Telemetry Generation**  
   - Installed and executed **LaZagne** on Windows Server
     
![LaZagne Executed](https://github.com/user-attachments/assets/79474fd0-d3a8-4f25-a3bd-3389a4deebe7)

   - Validated LaZagne events in the LimaCharlie console

![LaZagne Events](https://github.com/user-attachments/assets/cc76898e-33d8-43a3-b600-b626fda7329c)

## 🔄 Step 4: SOAR & Collaboration Integration  
1. **Tines SOAR**  
   - Ingested LimaCharlie alerts into Tines

- ### LimaCharlie Alerts Ingested into Tines

![Detection of LaZagne in tines](https://github.com/user-attachments/assets/e83c8a6a-fad4-43f2-8adc-85a3abe816e5)

- ### Complete Playbook Workflow in Tines

![Integration of Slack   Gmail](https://github.com/user-attachments/assets/340cf57e-2ae3-4c83-8372-c1fc51b98548)

   - Orchestrated multi‑channel actions (Slack, Gmail)
     
2. **Communication Channels**  
   - Configured Slack workspace notifications

- ### Slack Notification Setup for Automated Responses
  
![Slack Message](https://github.com/user-attachments/assets/f9811c7f-0713-4236-869c-c93d7e63879e)

   - Integrated Gmail for email alerts

- ### Gmail Integration for Incident Response Notifications
  
![Gmail](https://github.com/user-attachments/assets/cf02421c-94dc-4be9-9579-84369fd92134)

## 🎛️ Step 5: Playbook Automation & Decisioning  
| Trigger         | Human Prompt     | Action: “Yes”                      | Action: “No”                            |
|-----------------|------------------|------------------------------------|-----------------------------------------|
| LaZagne event   | “Isolate endpoint?” | 1. Isolate host via LimaCharlie<br>2. Slack: “Endpoint isolated” | 1. No isolation<br>2. Slack: “Investigate host” |

- ### User Prompt: Isolate Endpoint – Yes or No
![Prompted Yes No](https://github.com/user-attachments/assets/fb1ac3b4-59a2-4af5-8e6a-b3f3ae60233c)

- ### LimaCharlie – Real-Time Isolation Status
![Isolated](https://github.com/user-attachments/assets/7527e695-4f98-4b32-9766-de5436c5e9fb)

- ### Slack Notification: Endpoint Isolation Status
![Isolated Yes](https://github.com/user-attachments/assets/bbf9499a-4050-428f-895d-fba38aeb94fe)

## 🔑 Key Highlights  
- **Seamless EDR + SOAR**: LimaCharlie detection feeds Tines playbook  
- **User‑Driven Workflows**: Prompts in Slack drive containment decisions  
- **Rapid Isolation**: Automated endpoint quarantine via EDR API  
- **Multi‑Channel Alerts**: Slack & email ensure visibility  

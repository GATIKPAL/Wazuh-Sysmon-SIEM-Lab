<img width="1032" height="772" alt="wazuh ss" src="https://github.com/user-attachments/assets/01dc6963-eec8-4067-bf18-dc162ec22e06" /># Enterprise SIEM & Endpoint Detection Lab (Wazuh & Sysmon)

## Project Overview
This project demonstrates the deployment of a centralized security monitoring and threat detection environment using **Wazuh SIEM** and **Microsoft Sysmon**. The core objective was to configure continuous endpoint monitoring, capture granular system telemetry, and analyze live security events mapped to the **MITRE ATT&CK Framework**.

---

## System Architecture
- **SIEM Manager:** Wazuh Manager deployed on an Ubuntu Linux Virtual Machine (VirtualBox).
- **Monitored Endpoint:** Windows 11 Pro endpoint equipped with Wazuh Agent and Microsoft Sysmon telemetry.

---

## Key Implementation Steps & Detections

### 1. Centralized SIEM Configuration
Successfully deployed and verified the operational status of the centralized Wazuh Manager service on the Ubuntu server network.

<img width="691" height="607" alt="wazuh manager active" src="https://github.com/user-attachments/assets/b49f2947-44d5-4a52-bf0c-6a3fa55fa034" />

### 2. Endpoint Integration & Monitoring
Connected an active Windows 11 Pro endpoint (`My-PC` at `192.168.0.103`) to the Wazuh ecosystem for real-time log ingestion.
<img width="1028" height="768" alt="Screenshot 2026-05-18 112950" src="https://github.com/user-attachments/assets/423b752b-37b4-4db2-982d-5883992f890e" />
<img width="1026" height="762" alt="wazuh browser ss" src="https://github.com/user-attachments/assets/70d55011-b5c2-488b-828c-cdb60bbae96a" />

### 3. Threat Detection Scenarios (MITRE ATT&CK Mapping)

#### A. Process Injection (T1055)
- **Detection Method:** Leveraged Microsoft Sysmon to track deep system activities, successfully capturing **Sysmon Event ID 7 (Image Loaded)** within the Windows Event Viewer.
- **Log Evidence:** Triggered a dedicated rule flag identifying Process Injection techniques automatically parsed by the log collector.
<img width="1028" height="768" alt="Screenshot 2026-05-18 112950" src="https://github.com/user-attachments/assets/72b9e8c6-0112-47c1-9879-4ab04a5cbb7a" />


#### B. Account Discovery & Reconnaissance (T1087)
- **Detection Method:** Audited internal host command execution to detect local reconnaissance activities, specifically targeting unauthorized executions of the `net user` command.
- **Log Evidence:** Captured the corresponding JSON alert stream directly within the SIEM manager, classifying it as an active MITRE T1087 technique event.
<img width="720" height="96" alt="Screenshot 2026-05-18 114050" src="https://github.com/user-attachments/assets/441efa0d-5852-4515-966b-bbbfc9f8cb5b" />
<img width="720" height="96" alt="get user-on-ubuntu - Copy" src="https://github.com/user-attachments/assets/74e604b6-7600-4561-b532-736db667eeba" />

---

## Security Analytics Dashboard
Populated and monitored the centralized Wazuh Analytics overview dashboard, processing incoming telemetry, categorizing alerts under respective rule groups (SCA, Windows, Sysmon), and prioritizing triage-critical, **High-Severity (Level 12 or above)** alerts.
<img width="1032" height="772" alt="wazuh ss" src="https://github.com/user-attachments/assets/92f94974-12a4-4eee-aff8-ec2f9dc69d26" />

<img width="1022" height="767" alt="wazuh events ss" src="https://github.com/user-attachments/assets/56eb386f-306a-472e-8ac5-745daa698aa5" />


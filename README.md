# SOC-CloudLab

## Objective
Design and implement a Cloud SOC environment by deploying and configuring key security infrastructure components. This includes setting up ELK instances for centralized logging, deploying Windows and Linux servers to allow controlled brute-force attempts for log generation and rule development, and integrating Fleet Server with Elastic Agents for comprehensive monitoring. Additionally, deploy a Mythic Server to simulate various attack scenarios, establish an osTicket server integrated with Elasticsearch for streamlined alerting, and develop detection rules and alerts for identifying brute-force attacks on RDP and SSH.

## Network Diagram

![2025-03-07 10_07_55-SEC ANALYST drawio - draw io](https://github.com/user-attachments/assets/9bc9737c-75ac-49b3-bd72-512ae1d96d98)

## Deployed a Cloud SOC Environment through VULTR

![2025-03-07 10_08_54-Products - Vultr com](https://github.com/user-attachments/assets/68cda85e-0114-4bd6-a45d-c810017b646f)

### Skills Learned
- Configured a Virtual Private Cloud (VPC) environment to ensure secure, isolated communication between SOC components
- Configured Fleet Server and deployed Elastic Agents on Windows and Linux servers for comprehensive system monitoring and log forwarding
- Deployed and configured Elasticsearch, Logstash, and Kibana (ELK) for centralized log aggregation
- Designed and implemented a cloud-based Security Operations Center (SOC) to enhance threat monitoring and response capabilities.

### Tools Used
- Vultr, ELK, osTicket, Linux, Windows
  
## Deploy ELK instances (ElasticSearch & Kibana)
Download Elasticsearch & Kibana through the wget command on our Ubuntu Server
- Modify Elasticsearch and Kibana configuration files to allow access from our laptop instead of restricting it to localhost

![2025-03-06 20_15_30-root@ELK-CLOUD_ ~](https://github.com/user-attachments/assets/18af2303-a016-428b-9e3f-bbfcbe70ad70)
![2025-03-06 20_14_39-root@ELK-CLOUD_ ~](https://github.com/user-attachments/assets/44dfb5d1-821d-4cb0-a434-f5d066b37c12)
![2025-03-06 20_15_08-root@ELK-CLOUD_ ~](https://github.com/user-attachments/assets/3d457bc2-2ec5-40d9-a951-2f12b8642948)

systemctl daemon-reload & enable ElasticSearch.service and Kibana.service 
- Successfully accessed our Kibana instance via port 5601.
  
![2025-03-06 09_11_04-root@ELK-CLOUD_ ~](https://github.com/user-attachments/assets/73dacf66-cad4-4052-9c3f-6764ff8e1b18)
![2025-03-06 09_19_24-root@ELK-CLOUD_ ~](https://github.com/user-attachments/assets/3378c529-dcbe-46ad-9201-ffc267353d48)
![2025-03-06 09_22_11-Home - Elastic](https://github.com/user-attachments/assets/f8270a25-3579-48f8-ae9f-a5edbd9670df)

Resolved the "Failed to Retrieve Detection Engine Privileged" error by generating encryption keys and adding them to the keystore.

![2025-03-06 09_28_05-](https://github.com/user-attachments/assets/f4a4f4c2-7cfe-4545-b2b9-12a9eebb444b)
![2025-03-06 09_29_01-root@ELK-CLOUD_ _usr_share_kibana_bin](https://github.com/user-attachments/assets/59ec4d91-e14a-4a5c-89d1-3035275bff18)
![2025-03-06 09_29_36-Alerts - Kibana](https://github.com/user-attachments/assets/1ecc0b55-e7ff-49dd-bf57-80796fe02b51)

## Deploy Window & Linux Server with no Firewall (generate Sysmon logs in Window Server)
- I want to allow brute-force attempts on my system to generate logs, create alerts, and develop rules for detecting brute-force attacks on RDP and SSH in the future

Download Sysmon & Olaf raw configuration file on my Window Server
- Injest data into ElasticSearch by adding the integration into the Window Policy for Sysmon and Window Defender Logs(1116/1117/5001)

![2025-03-06 10_07_29-155 138 163 229 - Remote Desktop Connection](https://github.com/user-attachments/assets/cf931f6d-64b8-4de8-949e-df6af29b02ec)
![2025-03-06 10_25_46-window-policy - Agent policies - Fleet - Elastic](https://github.com/user-attachments/assets/0c8d333e-1bf8-4905-8323-64a6f5b83ea5)

## Deploy Fleet Server & Install Elastic Agents on Window/Linux Server
Fleet Server makes my life easier by managing mulitple Elastic Agents within a centralized location
- easy to update agent policies
- Elastic Agent uses port 8220 to communicate to the Fleet Server

![2025-03-06 09_54_29-noVNC (WINDOW-SERVER) - ID ae1f9a39-c62c-40c6-a618-8aec77ddc727](https://github.com/user-attachments/assets/967ed940-12df-4aaf-933a-2f63097bbebc)
![2025-03-07 09_39_47-Agents - Fleet - Elastic](https://github.com/user-attachments/assets/1656dcfb-4389-4c71-8a1e-178343540420)

## Deploy a Mythic Server to simulate various attacks on my other systems.
I'll be creating another repository on setting up Mythic C2 attacks, detecting them, and creating alerts.

## Deploy an osTicket server and integrate it with ElasticSearch
Download XAMPP & configure configuration files 
- allow Window Defender to allow inbound port connection to 80/443
- start Apache & SQL Server to go into Phpmyadmin (modify root/pma user accounts)

![2025-03-06 17_57_47-45 63 64 202 - Remote Desktop Connection](https://github.com/user-attachments/assets/60d8a4da-4e20-4ea6-ba46-76fb4dc59837)
![2025-03-06 18_11_30-45 63 64 202 - Remote Desktop Connection](https://github.com/user-attachments/assets/17d18567-8232-4b0c-a073-3dbd780f630b)

Download OSTICKET 
- create a osTicket database under PHPMYADMIN
- create helpdesk admin/user/pass on osTicket

![2025-03-06 19_29_54-45 63 64 202 - Remote Desktop Connection](https://github.com/user-attachments/assets/ca94436f-52d5-4fd1-a92a-a7ff0b2689cc)
![2025-03-06 19_33_58-45 63 64 202 - Remote Desktop Connection](https://github.com/user-attachments/assets/587edc39-ec12-4566-b18a-ac9cf0f313b5)

Add a Webhook Connector to the Elastic Agent to integrate osTicket with the ELK stack
- create a API key on osTicket
- edit the domain and key in the Webhook to match our private VPC osTicket configuration.

![2025-03-06 19_38_03-osTicket __ Admin Control Panel](https://github.com/user-attachments/assets/24401d1d-e0be-420d-b58d-ec9e5c22d8de)
![2025-03-06 19_54_15-Connectors - Elastic](https://github.com/user-attachments/assets/a8652ddf-28b8-468e-8b2e-dd6da70bc5d4)

## Add Elastic Defend (EDR) onto the Window Server 
Able to protect endpoints from malicious activity and isolate host

![2025-03-07 09_58_46-Endpoints - Kibana](https://github.com/user-attachments/assets/94cf196d-e139-4130-833c-1b797ce53682)








































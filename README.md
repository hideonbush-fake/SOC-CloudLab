# SOC-CloudLab

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





















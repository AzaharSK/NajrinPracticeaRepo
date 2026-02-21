## 1️⃣ What is Azure Storage?

__Microsoft Azure Storage is a scalable, durable, highly available cloud storage service used to store:__

- Files / pdf/ docs 
- Images / videos / Audio
- Logs
- Database-like NoSQL data
- Disks for VMs
- Backups

__Think of it as AWS S3 + EBS + DynamoDB + File Server combined in one ecosystem.__


# Azure Storage Account --- Feature Summary

## 10 Key Points

1.  **Non-relational storage support**\
    A storage account can store unstructured data (PDF, video, image,
    audio) without fixed schema --- unlike relational databases
    (rows/columns).

2.  **Multi-media unified storage**\
    One single Microsoft Azure Storage Account can hold mixed file types
    together in the same container.

3.  **Region placement matters (performance + cost)**\
    Storage should be created in the same region as the application
    (VM/WebApp) to reduce latency and cross-region traffic charges.

4.  **Account types (Standard vs Premium)**

    -   General Purpose v2 (Standard) → supports blobs, files, tables,
        queues\
    -   Premium → high-speed SSD, mainly blobs & files only

5.  **Redundancy options (data durability)**

    -   LRS → 3 copies in same datacenter\
    -   ZRS → 3 copies in different zones\
    -   GRS → 6 copies across regions\
    -   RA-GRS → secondary region read access

6.  **Security configuration**

    -   HTTPS-only access recommended\
    -   Key-based authentication default\
    -   Moving toward Microsoft Entra ID authentication\
    -   Optional anonymous access

7.  **Access tiers (cost optimization)**

    -   Hot → frequent read/write\
    -   Cool → rare access (backup/logs) cheaper storage but costly
        retrieval

8.  **Networking control**

    -   Public endpoint enabled by default\
    -   Can restrict to private network / selected VNets to prevent key
        leakage exposure

9.  **Data protection features**

    -   Soft delete (recover deleted files)\
    -   Versioning (keep all file versions)\
    -   Change feed (track modifications)\
    -   Immutability (cannot modify/delete once written)

10. **Encryption & key management**

-   Encryption enabled by default\
-   Microsoft-managed keys or customer-managed keys\
-   Optional double encryption (software + hardware disk encryption)

  
<img width="1705" height="1033" alt="image" src="https://github.com/user-attachments/assets/e23459cf-999f-486d-9622-610410cd3241" />
<img width="1346" height="1112" alt="image" src="https://github.com/user-attachments/assets/23de385a-08de-424f-93da-5a71c2bd7ddb" />
<img width="1192" height="1092" alt="image" src="https://github.com/user-attachments/assets/772036a9-d0c7-45c4-acdd-ae62dfb23a32" />
<img width="1345" height="1133" alt="image" src="https://github.com/user-attachments/assets/2ea01daf-b3c9-4ae8-b659-3fe180142c9a" />
<img width="983" height="1117" alt="image" src="https://github.com/user-attachments/assets/d0b2b7f5-2c08-4fc5-912d-d5ce58681e1b" />
<img width="1261" height="809" alt="image" src="https://github.com/user-attachments/assets/e0a6eb8c-af9a-4a2d-b448-e6175634a34a" />
<img width="1345" height="1133" alt="image" src="https://github.com/user-attachments/assets/a517b3aa-ac65-494e-9b27-47f5eed56d1f" />
<img width="1806" height="766" alt="image" src="https://github.com/user-attachments/assets/e72b0677-dda9-453a-90e2-4a20666e0f8f" />
<img width="1643" height="954" alt="image" src="https://github.com/user-attachments/assets/9ad418fd-d92f-45c5-9dbd-dd3b8d1ef5da" />

## Creating blob:
<img width="1844" height="1015" alt="image" src="https://github.com/user-attachments/assets/7acd6d35-4ba9-4cf9-924a-71acf06a9fa4" />
<img width="1846" height="773" alt="image" src="https://github.com/user-attachments/assets/dbdd168b-da6e-453a-aa5a-50f7db7652ed" />
<img width="1837" height="852" alt="image" src="https://github.com/user-attachments/assets/6d61289d-7f03-42a2-bd5a-ca241eb0b82c" />

### Generate SAS token
<img width="1781" height="1091" alt="image" src="https://github.com/user-attachments/assets/14e37274-4ab0-4106-828d-28f94c8d7043" />
<img width="1852" height="994" alt="image" src="https://github.com/user-attachments/assets/e0d348cd-2d2a-46dd-a775-61372025e092" />
<img width="1860" height="1102" alt="image" src="https://github.com/user-attachments/assets/11795068-6ada-4c8a-ab05-57daccc89772" />

```
https://appnewstorage.blob.core.windows.net/blob1/MVC.md?sp=r&st=2026-02-21T19:20:40Z&se=2026-02-22T03:35:40Z&sv=2024-11-04&sr=b&sig=TPqt7yHORGXOMJ%2FBcUxyHmQYHwSCvzxveKe3xXSd7%2FI%3D
```








# 🚀 Hotstar App CI/CD Deployment with Jenkins Master-Slave Architecture

This project sets up a full CI/CD pipeline for a Java-based Hotstar App using Jenkins, Maven, GitHub, Tomcat, and AWS S3. The pipeline is executed on a dedicated Jenkins slave node to ensure scalability and efficiency.

---

🔧 CI/CD Project Summary: Hotstar Web App Deployment with Jenkins Master-Slave Architecture
🛠️ Infrastructure Setup
You have configured a robust and production-grade Jenkins pipeline architecture using multiple virtual machines:

# 🖥️ Virtual Machines
1 Jenkins Master Node

2 Jenkins Slave Nodes (slave1, slave2)

1 Tomcat Web Server Node

## 🧰 Tech Stack

- **Jenkins** (Master + Slave Node)
- **Maven** – Compilation, Testing & Packaging
- **GitHub** – Source Code Repository
- **Tomcat** – Deployment Server
- **AWS S3** – Artifact Archival
- **AWS CLI** – For interacting with S3 from pipeline

---
✅ VM Configuration
| Node          | Installed Tools                                             |
| ------------- | ----------------------------------------------------------- |
| **Master**    | Git, Java, Maven, Jenkins (configured on port 8080)         |
| **Slaves**    | Git, Java, Maven, AWS CLI (configured with IAM access keys) |
| **Tomcat VM** | Java, Apache Tomcat Server (configured on port 8080)        |


## ⚙️ Pipeline Stages

1. **Git Checkout**
   - Clones the code from: `https://github.com/KastroVKiran/Hotstar-App.git`

2. **Code Compilation**
   - Uses: `mvn compile`

3. **Testing**
   - Executes: `mvn test`

4. **Packaging**
   - Builds `.war` file via: `mvn package`

5. **Deployment to Tomcat**
   - Uses Jenkins "Deploy to Container" plugin.
   - Target: `http://<Public_IP>:8080/`
   - Uses Jenkins credentials: `Tomcat-Creds`

6. **Artifact Archival**
   - Archives: `target/myapp.war` inside Jenkins job

7. **Upload to AWS S3**
   - Target Bucket: `s3-artifact-archivalstorage`
   - Uploads: `HotstarApp.war`
   - Region: `ap-south-1`
   - Credentials ID: `S3-creds`

---

## 🔐 Jenkins Credentials Configuration
Set up via Jenkins → Manage Credentials → (Global scope):

| ID             | Type                       | Usage                         |
| -------------- | -------------------------- | ----------------------------- |
| `Tomcat-Creds` | Username + Password        | Tomcat Manager App Deployment |
| `S3-creds`     | AWS Credentials            | Upload WAR file to S3 bucket  |
| `slave creds`  | SSH Username + Private Key | SSH access for Jenkins agents |

---
## 🔌 Jenkins Plugins Used
Installed via Manage Jenkins → Plugins:

| Plugin Name          | Purpose                                             |
| -------------------- | --------------------------------------------------- |
| AWS Steps            | For uploading artifacts to S3 from Jenkins pipeline |
| Deploy to Container  | For WAR deployment directly to Tomcat server        |
| AWS S3 Publisher     | Optional for publishing artifacts to S3             |
| Pipeline: Stage View | UI enhancement to visually track pipeline stages    |

---

##  🔗 Jenkins Nodes Configuration
Connected slave1 and slave2 via SSH using private key credentials

Configured labels (slave1, slave2) for distributed pipeline execution

Slave2 is specifically used for executing this pipeline ( Note: you can change it to any --> Jenkins will decide )

## 🙌 Special Thanks

Big thanks to **Kastro** for guidance and insights throughout this CI/CD journey.  

---

## 📷 Screenshots

![S3](https://github.com/user-attachments/assets/65187f8d-65a6-4ce2-aec6-f6d05a7ec99c)

![Script](https://github.com/user-attachments/assets/71472c58-6c1f-41ee-84a9-f496b8ed3412)

![Hotstar UI](https://github.com/user-attachments/assets/3ce4e79b-2179-4cb2-ba34-090f04f85434)


---

**Ganga Vaishnu Reddy**  
DevOps Enthusiast | Cloud Learner | Always Building 🚀

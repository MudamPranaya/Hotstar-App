# 🚀 Hotstar App CI/CD Deployment with Jenkins Master-Slave Architecture

This project sets up a full CI/CD pipeline for a Java-based Hotstar App using Jenkins, Maven, GitHub, Tomcat, and AWS S3. The pipeline is executed on a dedicated Jenkins slave node to ensure scalability and efficiency.

---

## 🧰 Tech Stack

- **Jenkins** (Master + Slave Node)
- **Maven** – Compilation, Testing & Packaging
- **GitHub** – Source Code Repository
- **Tomcat** – Deployment Server
- **AWS S3** – Artifact Archival
- **AWS CLI** – For interacting with S3 from pipeline

---

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
   - Target: `http://3.111.58.75:8080/`
   - Uses Jenkins credentials: `Tomcat-Creds`

6. **Artifact Archival**
   - Archives: `target/myapp.war` inside Jenkins job

7. **Upload to AWS S3**
   - Target Bucket: `s3-artifact-archivalstorage`
   - Uploads: `HotstarApp.war`
   - Region: `ap-south-1`
   - Credentials ID: `S3-creds`

---

## 🔧 Tools Installed on Jenkins Master/Slave Nodes & Tomcat Nodes

### Master Node:
- Jenkins Core
- Git
- Java

### Slave Node (`slave1` and `slave2`):
- Java
- Git
- Maven
- AWS CLI
  
### Tomcat Server :
- Java
- Tomcat
---

## 🔐 Jenkins Credentials

| ID            | Type            | Usage                     |
|---------------|------------------|----------------------------|
| `Tomcat-Creds`| Username/Password | Deploy to Tomcat          |
| `S3-creds`    | AWS Access Keys  | Upload to S3 via AWS CLI  |

---

## ✅ Plugins Required in Jenkins

- Git Plugin
- Maven Integration Plugin
- Pipeline Plugin
- Deploy to Container Plugin
- AWS CLI Plugin
- Credentials Plugin - AWS Steps

---

## 🙌 Special Thanks

Big thanks to **Kastro** for guidance and insights throughout this CI/CD journey.  
Also grateful to **AWS EC2** for providing the scalable infrastructure.

---

## 📷 Screenshots

![S3](https://github.com/user-attachments/assets/65187f8d-65a6-4ce2-aec6-f6d05a7ec99c)

![Script](https://github.com/user-attachments/assets/71472c58-6c1f-41ee-84a9-f496b8ed3412)

![Hotstar UI](https://github.com/user-attachments/assets/3ce4e79b-2179-4cb2-ba34-090f04f85434)


---

**Ganga Vaishnu Reddy**  
DevOps Enthusiast | Cloud Learner | Always Building 🚀

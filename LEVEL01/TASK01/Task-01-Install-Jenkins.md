# 🌟 **Task 01 - Install and Setup Jenkins Server**

[![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)](https://jenkins.io/)
[![RedHat](https://img.shields.io/badge/Red%20Hat-EE0000?style=for-the-badge&logo=redhat&logoColor=white)](https://redhat.com/)
[![DevOps](https://img.shields.io/badge/DevOps-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kodekloud.com/)

## 📌 **Task Description**

The **DevOps team** at **xFusionCorp Industries** is initiating the setup of **CI/CD pipelines** and has decided to utilize **Jenkins** as their server. The task involves installing Jenkins on a dedicated server and configuring the initial admin user.

**Requirements:**
1. Install **Jenkins** on the jenkins server using **yum utility only**
2. **Start Jenkins service** and ensure it's running
3. Create admin user with specific credentials:
   - **Username**: `theadmin`
   - **Password**: `Adm!n321`
   - **Full Name**: `Yousuf`
   - **Email**: `yousuf@jenkins.stratos.xfusioncorp.com`

👉 **Objective:** Set up a fully functional Jenkins server with proper admin user configuration for CI/CD pipeline development.

---

## 🔹 **Step-by-Step Solution**

### **🔹 Step 1: Connect to Jenkins Server**

```bash
# Connect to jenkins server from jump host
ssh root@jenkins
# Password: S3curePass
```

**Purpose**: Establish SSH connection to the Jenkins server using root credentials

**Access Details**:
- **Server**: jenkins
- **User**: root
- **Password**: S3curePass

---

### **🔹 Step 2: Install Required Dependencies**

```bash
# Install wget utility for downloading Jenkins repository
yum install wget -y

# Install Java (required for Jenkins)
sudo yum install fontconfig java-21-openjdk -y
```

**Purpose**: Install essential dependencies required for Jenkins installation

**Dependencies Installed**:
- **wget** - For downloading Jenkins repository configuration
- **fontconfig** - Required for Jenkins UI rendering
- **java-21-openjdk** - Java runtime environment for Jenkins

---

### **🔹 Step 3: Add Jenkins Repository**

```bash
# Download Jenkins repository configuration
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo

# Import Jenkins GPG key for package verification
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```

**Purpose**: Configure YUM package manager to access Jenkins official repository

**Repository Details**:
- **Source**: Official Jenkins RedHat stable repository
- **Security**: GPG key imported for package integrity verification

---

### **🔹 Step 4: Update Package Manager**

```bash
# Update system packages
sudo yum upgrade -y
```

**Purpose**: Ensure all system packages are up-to-date before Jenkins installation

---

### **🔹 Step 5: Install Jenkins**

```bash
# Install Jenkins using yum
sudo yum install jenkins -y
```

**Purpose**: Install Jenkins server package using YUM package manager as required

**Expected Output**:
```
Installing:
 jenkins    x86_64    2.528-1.1    jenkins    [size]

Complete!
```

---

### **🔹 Step 6: Configure and Start Jenkins Service**

```bash
# Reload systemd daemon to recognize Jenkins service
sudo systemctl daemon-reload

# Enable Jenkins service to start automatically on boot
sudo systemctl enable jenkins

# Start Jenkins service
sudo systemctl start jenkins

# Check Jenkins service status
sudo systemctl status jenkins
```

**Purpose**: Configure Jenkins as a system service and start it

**Expected Output**:
```
● jenkins.service - Jenkins Continuous Integration Server
   Loaded: loaded (/usr/lib/systemd/system/jenkins.service; enabled)
   Active: active (running)
   Main PID: [PID] (java)
```

**Status**: ✅ **Jenkins service is running successfully**

---

## 📸 **Visual Documentation**

### **Jenkins Initial Setup - Plugin Installation**

![Jenkins Plugin Selection](screenshot-1)
*Screenshot 1: Jenkins Customize page showing plugin installation options*

- **Option Selected**: "Install suggested plugins" 
- **Purpose**: Installs community-recommended plugins for standard Jenkins functionality

### **Jenkins Plugin Installation Progress**

![Jenkins Plugin Installation](screenshot-2) 
*Screenshot 2: Jenkins plugin installation in progress*

**Plugins Being Installed**:
- ✅ **Folders** - Organize projects in folders
- ✅ **Timestamper** - Add timestamps to console output  
- ✅ **OWASP Markup Formatter** - Security formatting
- ✅ **Build Timeout** - Timeout build configurations
- ✅ **Credentials Binding** - Secure credential management
- ✅ **Workspace Cleanup** - Clean workspace after builds
- ✅ **Ant** - Apache Ant build tool integration
- ✅ **Gradle** - Gradle build tool support

### **Admin User Creation**

![Jenkins Admin User Setup](screenshot-3)
*Screenshot 3: Creating the first admin user with specified credentials*

**Admin User Configuration**:
- **Username**: `theadmin` ✅
- **Password**: `Adm!n321` ✅ (Hidden for security)
- **Full Name**: `Yousuf` ✅
- **Email**: *yousuf@jenkins.stratos.xfusioncorp.com* (as required)

### **Jenkins Dashboard - Installation Complete**

![Jenkins Dashboard](screenshot-4)
*Screenshot 4: Successfully configured Jenkins dashboard*

**Dashboard Features Visible**:
- ✅ **Welcome Message** - "Welcome to Jenkins!"
- ✅ **Create a Job** - Option to create new CI/CD jobs
- ✅ **Build Queue** - No builds in queue (clean installation)
- ✅ **Build Executor Status** - 0/2 executors available
- ✅ **Navigation Menu** - New Item, Build History, Manage Jenkins, My Views

---

## 📋 **Quick Command Reference**

```bash
# Complete installation script for Jenkins
ssh root@jenkins

# Install dependencies
yum install wget -y
sudo yum install fontconfig java-21-openjdk -y

# Add Jenkins repository
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

# Install and start Jenkins
sudo yum upgrade -y
sudo yum install jenkins -y
sudo systemctl daemon-reload
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins

# Access Jenkins UI via browser and complete setup
```

---

## 💡 **Key Learning Points**

- 🎯 **Repository Management**: Understanding how to add external repositories to YUM package manager
- 🔧 **Service Management**: Using systemctl commands for service lifecycle management  
- 🚀 **Security Best Practices**: Importing GPG keys for package verification and creating secure admin credentials
- 📊 **Plugin Architecture**: Jenkins extensibility through plugin ecosystem for enhanced functionality
- 🛡️ **Initial Configuration**: Importance of proper initial setup for production-ready CI/CD infrastructure

---

## 🔧 **Troubleshooting Guide**

### **Issue 1: Jenkins Service Timeout**
**Symptoms**: Jenkins service fails to start within timeout period
**Solution**: Increase service timeout or check system resources
```bash
# Check system resources
free -h
df -h

# Restart Jenkins with extended timeout
sudo systemctl restart jenkins
sudo systemctl status jenkins
```

### **Issue 2: Java Not Found Error**
**Symptoms**: Jenkins installation fails due to missing Java
**Solution**: Install appropriate Java version
```bash
# Install Java 11 or 21
sudo yum install java-21-openjdk -y
# Verify Java installation
java -version
```

### **Issue 3: Repository Access Issues**
**Symptoms**: Unable to download Jenkins packages
**Solution**: Verify internet connectivity and repository configuration
```bash
# Test repository access
curl -I https://pkg.jenkins.io/redhat-stable/jenkins.repo
# Re-add repository if needed
sudo rm /etc/yum.repos.d/jenkins.repo
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
```

### **Issue 4: Port 8080 Already in Use**
**Symptoms**: Jenkins cannot bind to default port 8080
**Solution**: Change Jenkins port or stop conflicting service
```bash
# Check what's using port 8080
sudo lsof -i :8080
# Stop conflicting service or change Jenkins port
sudo systemctl edit jenkins
# Add: Environment="JENKINS_PORT=8081"
```

---

## 🚨 **Challenge & Solution Summary**

**🔍 Main Challenge:**
Setting up Jenkins server from scratch using YUM package manager while ensuring all dependencies are properly installed and configured, followed by secure admin user creation.

**💡 Solution Approach:**
1. **Dependency Management**: Installed required packages (wget, Java, fontconfig) before Jenkins installation
2. **Repository Configuration**: Added official Jenkins repository with proper GPG key verification  
3. **Service Management**: Used systemctl commands for proper service lifecycle management
4. **Security Setup**: Created admin user with strong credentials as per organizational requirements
5. **Plugin Installation**: Selected suggested plugins for comprehensive Jenkins functionality

**🎯 Key Success Factors:**
- **Proper sequencing** of installation steps to avoid dependency conflicts
- **Repository verification** using GPG keys for security compliance
- **Service enablement** ensuring Jenkins starts automatically on system reboot  
- **Admin user security** following best practices for credential management
- **Plugin selection** installing community-recommended plugins for standard CI/CD operations

**⚠️ Critical Configuration Details:**
- **Java compatibility** ensuring Java 21 OpenJDK installation for Jenkins 2.528
- **Repository source** using official Jenkins stable repository for reliable updates
- **Service configuration** enabling auto-start and daemon reload for proper service registration
- **User credentials** implementing specified admin credentials for organizational compliance
- **Plugin installation** selecting suggested plugins for comprehensive functionality

---

## ⚠️ **Production Considerations**

🔧 **Service Management**: Jenkins is now configured as a systemd service with auto-start enabled

🔐 **Security Implementation**: Admin user created with strong password and proper email configuration

📊 **Resource Monitoring**: Monitor system resources as Jenkins usage grows

🛡️ **Backup Strategy**: Plan for Jenkins configuration and job backup procedures

🚀 **Scaling Preparation**: Consider distributed build setup for larger development teams

---

## 🏆 **Task Completion Status**

- ✅ **Jenkins Installation Complete** - Using YUM package manager as required
- ✅ **Service Started Successfully** - Jenkins running on default port 8080
- ✅ **Admin User Created** - theadmin user with specified credentials
- ✅ **Plugin Installation Done** - Suggested plugins installed and configured  
- ✅ **Dashboard Accessible** - Ready for CI/CD job creation
- ✅ **All Requirements Met** - Task completed according to specifications

---

*📝 **Note**: This Jenkins installation provides a solid foundation for CI/CD pipeline development. The server is now ready for creating build jobs, configuring source control integration, and implementing automated deployment workflows.*
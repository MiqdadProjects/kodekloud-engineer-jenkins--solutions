# 🌟 **Task 05 - Create Jenkins Job to Install Packages**

[![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)](https://jenkins.io/)
[![SSH Plugin](https://img.shields.io/badge/SSH_Plugin-45B7D1?style=for-the-badge&logo=ssh&logoColor=white)](https://plugins.jenkins.io/ssh/)
[![SSH Credentials](https://img.shields.io/badge/SSH_Credentials-4ECDC4?style=for-the-badge&logo=key&logoColor=white)](https://plugins.jenkins.io/ssh-credentials/)
[![SSH Build Agents](https://img.shields.io/badge/SSH_Build_Agents-FF6B6B?style=for-the-badge&logo=server&logoColor=white)](https://plugins.jenkins.io/ssh-agent/)

## 📌 **Task Description**

The **Nautilus DevOps team** under **Stratos Datacenter** aims to automate package installation on the storage server using a Jenkins job. The task involves creating a Jenkins job to install packages specified via a parameter on the storage server.

**Requirements:**
1. **Access Jenkins UI** using admin credentials (`admin` / `Adm!n321`).
2. **Create a Jenkins job** named `install-packages` with the following specifications:
   - Add a string parameter named `PACKAGE`.
   - Configure the job to install the package specified in the `$PACKAGE` parameter on the storage server in Stratos Datacenter.

**Notes:**
- Install required plugins (e.g., SSH, SSH Credentials, SSH Build Agents) and restart Jenkins if necessary, opting for "Restart Jenkins when installation is complete and no jobs are running."
- Verify the job runs successfully on repeated executions for reliability.
- Capture screenshots (or use screen recording software like loom.com) for documentation.
- Ensure connectivity to the storage server (`ststor01`) via SSH for package installation.

👉 **Objective:** Automate package installation on the storage server using a parameterized Jenkins job for efficient and reliable execution.

---

## 🔹 **Step-by-Step Solution**

### **🔹 Step 1: Access Jenkins UI**

 CLICK ON JENKINS BUTTON AND LOGIN

**Login Details**:
```
Username: admin
Password: Adm!n321
```

**Navigation Path**: Open Jenkins UI → Enter credentials → Click **Sign in**

**Purpose**: Authenticate as the admin user to access Jenkins management features.

---

### **🔹 Step 2: Verify Storage Server Connectivity**



**SSH Login Process** (from terminal):
```
ssh natasha@ststor01
```

**Purpose**: Confirm connectivity to the storage server (`ststor01`) to ensure Jenkins can execute commands remotely.

**Note**: Ensure SSH access is configured correctly for the user `natasha` on the storage server.

---

### **🔹 Step 3: Install Required Plugins**

![Plugin Manager] ![screenshot: 1](<task 5 (1).png>)
*Screenshot 1: Plugin Manager showing installation of SSH plugins*

**Plugin Installation Process**:
```
1. Navigate to: Manage Jenkins → Plugins
2. Select: Available Plugins tab
3. Search for: "ssh", "ssh credentials", "ssh build agents"
4. Install the following plugins:
   - SSH Plugin
   - SSH Credentials Plugin
   - SSH Build Agents Plugin
5. Select: Restart Jenkins when installation is complete and no jobs are running
```

**Plugin Details**:
- **SSH Plugin**: Enables executing commands on remote servers via SSH.
- **SSH Credentials Plugin**: Manages SSH credentials for secure connections.
- **SSH Build Agents Plugin**: Supports SSH-based build agents for remote execution.
- **Post-Installation**: Jenkins restarts to apply plugins.

**Note**: If the Jenkins UI becomes unresponsive post-restart, refresh the page.

---

### **🔹 Step 4: Configure SSH Credentials**

![SSH Credentials Setup] ![screenshot: 2](<task 5 (2).png>) ![screenshot: 3](<task 5 (3).png>) 
*Screenshot 2 and 3 : Credentials page showing SSH credentials creation*

**Credentials Creation Process**:
```
1. Navigate to: Manage Jenkins → Credentials → System → Global credentials (unrestricted)
2. Click: Add Credentials
3. Configure:
   - Kind: SSH Username with private key
   - Username: natasha
   - Private Key: Enter directly (or upload key for ststor01)
   - Passphrase: (Leave blank or enter if required)
   - ID: ststor01-ssh (optional, for reference)
   - Description: SSH credentials for ststor01
4. Click: OK
```

**Purpose**: Add SSH credentials for secure communication with the storage server.

---

### **🔹 Step 5: Configure SSH Remote Host**

![SSH Remote Host Setup] ![screenshot: 4](<task 5 (4).png>) 
*Screenshot 3: System configuration showing SSH remote host addition*

**SSH Host Configuration Process**:
```
1. Navigate to: Manage Jenkins → System
2. Scroll to: SSH remote hosts
3. Add Host:
   - Hostname: ststor01
   - Credentials: Select natasha (ststor01-ssh credentials)
4. Click: Check Connection
5. Verify: Connection successful
6. Click: Save
```

**Purpose**: Configure the storage server as a remote host for SSH-based job execution.

---

### **🔹 Step 6: Create Jenkins Job `install-packages`**

![Job Creation] ![screenshot: 5](<task 5(5).png>)
*Screenshot 6: New job creation for install-packages*

**Job Creation Process**:
```
1. Navigate to: Jenkins Dashboard → New Item
2. Enter Item Name: install-packages
3. Select: Freestyle project
4. Click: OK
```

**Job Configuration**:
```
1. General:
   - Check: This project is parameterized
   - Add Parameter: String Parameter
     - Name: PACKAGE
     - Default Value: (Leave blank or set to e.g., nginx)
2. Build Steps:
   - Add build step: Execute shell script on remote host using SSH
   - Configure:
     - SSH site: ststor01
     - Command: 
       ```
       sudo yum install -y $PACKAGE
       ```
3. Click: Save
```

**Purpose**: Create a parameterized job to install the specified package on the storage server.

---

### **🔹 Step 7: Test Job Execution**

![Build with Parameters] ![screenshot: 6](<task 5 (6).png>)
*Screenshot 7: Build with Parameters page showing nginx package build*

**Build Execution Process**:
```
1. Navigate to: Jenkins Dashboard → install-packages
2. Click: Build with Parameters
3. Enter: PACKAGE = nginx
4. Click: Build
5. Verify build success in Build History
```

**Validation on Storage Server** (via terminal):
```
ssh natasha@ststor01
nginx -v
```
**Expected Output**:
```
nginx version: nginx/1.20.1
```

**Purpose**: Confirm the job installs the specified package and runs reliably on repeated executions.

---

## 📋 **Quick Command Reference**

**UI Navigation Sequence**:
```
1. Open Jenkins UI → Login (admin/Adm!n321)
2. Manage Jenkins → Plugins → Available Plugins
   - Search: "ssh", "ssh credentials", "ssh build agents"
   - Install: SSH Plugin, SSH Credentials Plugin, SSH Build Agents Plugin
   - Select: Restart Jenkins when installation is complete and no jobs are running
3. Manage Jenkins → Credentials → System → Global credentials
   - Add Credentials:
     - Kind: SSH Username with private key
     - Username: natasha
     - Private Key: (Enter key for ststor01)
     - ID: ststor01-ssh
   - Save
4. Manage Jenkins → System → SSH remote hosts
   - Add: ststor01 with natasha credentials
   - Check Connection → Save
5. Jenkins Dashboard → New Item
   - Name: install-packages
   - Type: Freestyle project
   - Parameter: String Parameter (Name: PACKAGE)
   - Build Step: Execute shell script on remote host using SSH
     - SSH site: ststor01
     - Command: sudo yum install -y $PACKAGE
   - Save
6. install-packages → Build with Parameters
   - PACKAGE: nginx
   - Build
7. SSH to ststor01: ssh natasha@ststor01
   - Verify: nginx -v
```

---

## 💡 **Key Learning Points**

- 🎯 **Parameterized Jobs**: Using string parameters to make Jenkins jobs flexible and reusable.
- 🔧 **SSH Integration**: Configuring SSH plugins for remote execution on servers like `ststor01`.
- 🚀 **Plugin Management**: Installing and managing SSH-related plugins for Jenkins automation.
- 📊 **Job Reliability**: Ensuring jobs execute consistently across multiple runs.
- 🛡️ **Secure Execution**: Using SSH credentials for secure remote command execution.

---

## 🔧 **Troubleshooting Guide**

### **Issue 1: SSH Plugins Not Found**
**Symptoms**: SSH-related plugins not listed in available plugins.
**Solution**: Refresh plugin data or check connectivity.
```
1. Manage Jenkins → Plugins → Advanced
2. Click: Check now (refresh plugin list)
3. Search again for "SSH", "SSH Credentials", "SSH Build Agents"
```

### **Issue 2: SSH Connection to ststor01 Fails**
**Symptoms**: "Check Connection" fails for ststor01.
**Solution**: Verify credentials and network connectivity.
```
1. Confirm: SSH key for natasha is correct
2. Test: ssh natasha@ststor01 from terminal
3. Re-add credentials in Jenkins if needed
```

### **Issue 3: Job Fails to Install Package**
**Symptoms**: Package installation fails during job execution.
**Solution**: Check command syntax and permissions.
```
1. Verify: Command is sudo yum install -y $PACKAGE
2. Check: natasha has sudo privileges on ststor01
3. Test: Run sudo yum install -y nginx manually on ststor01
```

### **Issue 4: Jenkins UI Unresponsive After Restart**
**Symptoms**: UI does not load after plugin installation restart.
**Solution**: Refresh browser or wait.
```
1. Refresh the Jenkins UI page
2. If issue persists, check Jenkins service status
3. Restart Jenkins manually if necessary
```

---

## 🚨 **Challenge & Solution Summary**

**🔍 Main Challenge:**
Creating a Jenkins job to automate package installation on the storage server (`ststor01`) using a parameterized approach, ensuring SSH connectivity, plugin installation, and reliable job execution.

**💡 Solution Approach:**
1. **Login**: Accessed Jenkins UI with admin credentials.
2. **Plugin Installation**: Installed SSH, SSH Credentials, and SSH Build Agents plugins.
3. **SSH Configuration**: Added SSH credentials and configured `ststor01` as a remote host.
4. **Job Creation**: Created `install-packages` job with a `PACKAGE` string parameter and SSH build step.
5. **Execution and Validation**: Ran job with `nginx` parameter and verified installation on `ststor01`.

**🎯 Key Success Factors:**
- **Plugin Dependency**: Installed required SSH plugins before job configuration.
- **SSH Setup**: Ensured secure and functional SSH connectivity to `ststor01`.
- **Parameterization**: Used `PACKAGE` parameter for flexible package installation.
- **Reliability Testing**: Validated job success with repeated executions.
- **Documentation**: Captured screenshots for verification.

**⚠️ Critical Configuration Details:**
- **SSH Plugins**: Essential for remote execution on `ststor01`.
- **Credentials Security**: Proper SSH key configuration for `natasha`.
- **Sudo Privileges**: Ensured `natasha` has necessary permissions on `ststor01`.
- **Job Parameter**: Correctly configured `PACKAGE` for dynamic package installation.
- **Command Syntax**: Used `sudo yum install -y $PACKAGE` for reliable package installation.

---

## ⚠️ **Production Considerations**

🔧 **Job Scalability**: Extend the job to handle multiple packages or servers.  
🔐 **Security**: Store SSH keys securely and limit sudo access on `ststor01`.  
📊 **Monitoring**: Log job executions to track package installations.  
🛡️ **Backup**: Backup Jenkins configuration before plugin or job changes.  
🚀 **Automation**: Integrate job with CI/CD pipelines for broader automation.

---

## 🏆 **Task Completion Status**

- ✅ **Admin Login Successful** - Accessed Jenkins UI with admin credentials.
- ✅ **Plugins Installed** - Installed SSH, SSH Credentials, and SSH Build Agents plugins.
- ✅ **SSH Configured** - Added `ststor01` as remote host with `natasha` credentials.
- ✅ **Job Created** - Created `install-packages` job with `PACKAGE` parameter.
- ✅ **Job Executed** - Successfully installed `nginx` on `ststor01` and verified.
- ✅ **All Requirements Met** - Automated package installation as specified.

---

## 🚀 **Job Configuration Summary**

### **Current Job Configuration**

| Job Name | Parameter | Remote Host | Command | Purpose |
|----------|-----------|-------------|---------|---------|
| **install-packages** | PACKAGE (String) | ststor01 | `sudo yum install -y $PACKAGE` | Install specified package on storage server |

### **Features Implemented**

- 🔐 **Parameterized Job**: Configured with `PACKAGE` string parameter.
- 🛡️ **SSH Execution**: Remote command execution on `ststor01` via SSH.
- 👥 **Plugin Support**: Installed SSH-related plugins for functionality.
- 📊 **Reliable Execution**: Validated job success with `nginx` installation.
- 🚫 **Secure Access**: Used SSH credentials for secure communication.

---

*📝 **Note**: This Jenkins job automates package installation on the storage server, providing a scalable and reusable solution for the Nautilus DevOps team. The SSH-based execution ensures secure and reliable automation, with the parameterized approach allowing flexibility for installing various packages as needed.*
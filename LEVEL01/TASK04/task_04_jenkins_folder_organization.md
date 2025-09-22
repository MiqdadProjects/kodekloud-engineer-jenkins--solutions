# 🌟 **Task 04 - Organize Jenkins Jobs into Folders**

[![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)](https://jenkins.io/)
[![Folder Plugin](https://img.shields.io/badge/Folder_Plugin-45B7D1?style=for-the-badge&logo=folder&logoColor=white)](https://plugins.jenkins.io/cloudbees-folder/)

## 📌 **Task Description**

The **xFusionCorp Industries DevOps team** aims to streamline the management of **Jenkins jobs** by organizing them into distinct folders based on their purpose. The task involves creating a folder structure within Jenkins and moving existing jobs to the appropriate folder.

**Requirements:**
1. **Access Jenkins UI** using admin credentials (`admin` / `Adm!n321`).
2. **Create a new folder** named `Apache` within the Jenkins UI.
3. **Move existing jobs** `httpd-php` and `services` into the newly created `Apache` folder.

**Notes:**
- Install any required plugins (e.g., Folders plugin) and restart Jenkins if necessary, opting for "Restart Jenkins when installation is complete and no jobs are running."
- Jenkins UI may become temporarily unresponsive during service restart; refresh the page if needed.
- Capture screenshots (or use screen recording software like loom.com) for documentation and review.

👉 **Objective:** Organize Jenkins jobs into a folder structure to improve management and scalability.

---

## 🔹 **Step-by-Step Solution**

### **🔹 Step 1: Access Jenkins UI**



**Login Details**:
```
Username: admin
Password: Adm!n321
```

**Navigation Path**: Open Jenkins UI → Enter credentials → Click **Sign in**

**Purpose**: Authenticate as the admin user to access Jenkins management features.

---

### **🔹 Step 2: Install Folders Plugin**

![Plugin Manager] ![screenshot: 1](<TASK 4 (1).png>)
*Screenshot 1: Plugin Manager showing Folders plugin installation*

**Plugin Installation Process**:
```
1. Navigate to: Manage Jenkins → Plugins
2. Select: Available Plugins tab
3. Search for: "folders"
4. Locate: CloudBees Folders Plugin
5. Install the plugin
6. Select: Restart Jenkins when installation is complete and no jobs are running
```

**Plugin Details**:
- **Name**: CloudBees Folders Plugin
- **Category**: Folder Management
- **Description**: Enables organizing jobs into folders for better management
- **Post-Installation**: Jenkins restarts to apply the plugin

**Note**: If the Jenkins UI becomes unresponsive post-restart, refresh the page.

---

### **🔹 Step 3: Create Apache Folder**

![New Folder Creation] ![screenshot:2](<TASK 4 (2).png>) click on new item  ,
 ![screenshot:3](<TASK 4 (3).png>) click on free style project.
*Screenshot 2: New Item page showing Apache folder creation*

**Folder Creation Process**:
```
1. Navigate to: Jenkins Dashboard → New Item
2. Enter Item Name: Apache
3. Select: Folder
4. Click: OK
5. Configure folder (optional, default settings suffice)
6. Click: Save
```

**Folder Details**:
- **Name**: Apache
- **Type**: Folder
- **Purpose**: Organize related jobs (`httpd-php` and `services`)

**Purpose**: Create a dedicated folder to group Apache-related jobs.

---

### **🔹 Step 4: Move Jobs to Apache Folder**

![Move Jobs] ! ![screenshot: 4](<TASK 4 (4).png>)
*Screenshot 4: Moving httpd-php and services jobs to Apache folder*

**Job Movement Process**:
```
1. Navigate to: Jenkins Dashboard
2. Select job: httpd-php
3. Click: Move
4. Select destination: Jenkins → Apache
5. Confirm move
6. Repeat for job: services
```

**Jobs Moved**:
- **httpd-php**: Moved to `Jenkins → Apache`
- **services**: Moved to `Jenkins → Apache`

**Purpose**: Organize existing jobs into the `Apache` folder for streamlined management.

---

## 📋 **Quick Command Reference**

**UI Navigation Sequence**:
```
1. Open Jenkins UI → Login (admin/Adm!n321)
2. Manage Jenkins → Plugins → Available Plugins
   - Search: "folders"
   - Install: CloudBees Folders Plugin
   - Select: Restart Jenkins when installation is complete and no jobs are running
3. Jenkins Dashboard → New Item
   - Name: Apache
   - Type: Folder
   - Click: OK → Save
4. For each job (httpd-php, services):
   - Select job → Move
   - Choose: Jenkins → Apache
   - Confirm
```

---

## 💡 **Key Learning Points**

- 🎯 **Folder Organization**: Using folders to group related Jenkins jobs improves scalability and management.
- 🔧 **Plugin Dependency**: The CloudBees Folders Plugin is essential for folder-based job organization.
- 🚀 **Job Management**: Moving jobs into folders maintains their functionality while improving structure.
- 📊 **UI Navigation**: Familiarity with Jenkins UI for plugin installation, folder creation, and job management.
- 🛡️ **Service Restart**: Handling Jenkins restarts and UI refresh for plugin activation.

---

## 🔧 **Troubleshooting Guide**

### **Issue 1: Folders Plugin Not Found**
**Symptoms**: "Folders" plugin not listed in available plugins.
**Solution**: Refresh plugin data or check connectivity.
```
1. Manage Jenkins → Plugins → Advanced
2. Click: Check now (refresh plugin list)
3. Search again for "CloudBees Folders Plugin"
```

### **Issue 2: Jenkins UI Unresponsive After Restart**
**Symptoms**: UI does not load after plugin installation restart.
**Solution**: Refresh the browser or wait a few minutes.
```
1. Refresh the Jenkins UI page
2. If issue persists, check Jenkins service status
3. Restart Jenkins manually if necessary
```

### **Issue 3: Jobs Not Moving to Folder**
**Symptoms**: Jobs remain in root directory after move attempt.
**Solution**: Verify folder exists and user has permissions.
```
1. Confirm: Apache folder exists in Jenkins Dashboard
2. Check: Admin user has full permissions
3. Retry: Select job → Move → Jenkins → Apache
```

### **Issue 4: Folder Creation Fails**
**Symptoms**: Unable to create Apache folder.
**Solution**: Ensure Folders plugin is installed and activated.
```
1. Verify: CloudBees Folders Plugin is installed (Manage Jenkins → Plugins → Installed Plugins)
2. Check: Jenkins has restarted post-installation
3. Retry: New Item → Folder → Apache
```

---

## 🚨 **Challenge & Solution Summary**

**🔍 Main Challenge:**
Organizing Jenkins jobs into a folder structure by creating an `Apache` folder and moving `httpd-php` and `services` jobs into it, ensuring proper plugin installation and handling potential UI issues during Jenkins restart.

**💡 Solution Approach:**
1. **Login**: Accessed Jenkins UI with admin credentials.
2. **Plugin Installation**: Installed CloudBees Folders Plugin with Jenkins restart.
3. **Folder Creation**: Created `Apache` folder via New Item interface.
4. **Job Movement**: Moved `httpd-php` and `services` jobs into the `Apache` folder.
5. **Validation**: Ensured folder structure and job organization meet requirements.

**🎯 Key Success Factors:**
- **Plugin Installation**: Ensured Folders plugin was installed before folder creation.
- **Sequential Workflow**: Completed login, plugin installation, folder creation, and job movement in order.
- **UI Handling**: Managed potential UI unresponsiveness with page refresh.
- **Permission Awareness**: Admin user credentials ensured full access for all operations.
- **Documentation**: Captured screenshots for verification.

**⚠️ Critical Configuration Details:**
- **Folders Plugin**: Required for folder functionality in Jenkins.
- **Admin Access**: Full permissions needed for plugin installation and job movement.
- **Restart Handling**: Proper restart management to avoid job interruptions.
- **Job Integrity**: Moving jobs does not affect their configuration or functionality.
- **Folder Naming**: Exact name `Apache` used to meet requirements.

---

## ⚠️ **Production Considerations**

🔧 **Folder Structure**: Plan folder hierarchy based on team and project needs.  
🔐 **Access Control**: Apply folder-level permissions for team-specific access (e.g., using Matrix Authorization).  
📊 **Job Monitoring**: Regularly review folder contents for organization and relevance.  
🛡️ **Backup Strategy**: Backup Jenkins configuration before major changes like plugin installations.  
🚀 **Scalability**: Use folders to support growing CI/CD pipelines with multiple teams.

---

## 🏆 **Task Completion Status**

- ✅ **Admin Login Successful** - Accessed Jenkins UI with admin credentials.
- ✅ **Folders Plugin Installed** - CloudBees Folders Plugin installed and Jenkins restarted.
- ✅ **Apache Folder Created** - New folder named `Apache` created in Jenkins.
- ✅ **Jobs Moved** - `httpd-php` and `services` jobs moved to `Apache` folder.
- ✅ **All Requirements Met** - Folder structure implemented as specified.

---

## 🚀 **Folder Organization Summary**

### **Current Folder Structure**

| Folder | Jobs Included | Purpose |
|--------|---------------|---------|
| **Apache** | httpd-php, services | Group Apache-related jobs for streamlined management |

### **Features Implemented**

- 🔐 **Folder Creation**: `Apache` folder created for job organization.
- 🛡️ **Job Organization**: Moved `httpd-php` and `services` to `Apache` folder.
- 👥 **Plugin Support**: Installed CloudBees Folders Plugin for folder functionality.
- 📊 **Scalable Structure**: Foundation for further folder-based job management.
- 🚫 **UI Management**: Handled potential restart-related UI issues.

---

*📝 **Note**: This folder-based organization enhances Jenkins job management by grouping related jobs, improving scalability and clarity for the xFusionCorp Industries DevOps team. The CloudBees Folders Plugin enables future expansion of folder structures as CI/CD pipelines grow.*
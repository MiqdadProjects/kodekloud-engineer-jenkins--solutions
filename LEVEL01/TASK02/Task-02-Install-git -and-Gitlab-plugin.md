# 🌟 **Task 02 - Install Git and GitLab Plugins**

[![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)](https://jenkins.io/)
[![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)](https://git-scm.com/)
[![GitLab](https://img.shields.io/badge/GitLab-FCA326?style=for-the-badge&logo=gitlab&logoColor=white)](https://gitlab.com/)
[![Plugin](https://img.shields.io/badge/Plugins-4285F4?style=for-the-badge&logo=jenkins&logoColor=white)](https://plugins.jenkins.io/)

## 📌 **Task Description**

The **Nautilus DevOps team** has recently setup a **Jenkins server** and wants to install essential plugins that will be used in most CI/CD jobs. The task focuses on installing **Git** and **GitLab** plugins to enable source code management and GitLab integration capabilities.

**Requirements:**
1. **Access Jenkins UI** using admin credentials
   - **Username**: `admin`  
   - **Password**: `Adm!n321`
2. **Install Git and GitLab plugins** from the available plugins repository
3. **Restart Jenkins service** if required to complete plugin installation
4. **Verify plugin installation** in the installed plugins section

👉 **Objective:** Configure Jenkins with essential SCM plugins to enable Git and GitLab integration for CI/CD pipelines.

---

## 🔹 **Step-by-Step Solution**

### **🔹 Step 1: Access Jenkins Dashboard**

![Jenkins Dashboard] ![screenshot:1](<task 2.png>)
*Screenshot 1: Jenkins main dashboard with navigation menu*

**Navigation Path**: Dashboard → **Manage Jenkins** (highlighted in blue)

**Purpose**: Access Jenkins administration interface for plugin management

**Dashboard Elements Visible**:
- ✅ **Welcome Message** - "Welcome to Jenkins!"
- ✅ **Navigation Menu** - Manage Jenkins option highlighted
- ✅ **Build Queue** - Empty (no active builds)
- ✅ **Build Executor Status** - 0/2 executors available

---

### **🔹 Step 2: Navigate to Plugin Management**

**Click Path**: `Manage Jenkins` → `Plugins`

**Purpose**: Access the plugin management interface where you can install, update, and manage Jenkins plugins

**Plugin Management Sections**:
- **Updates** - Available plugin updates
- **Available plugins** - All plugins available for installation
- **Installed plugins** - Currently installed plugins
- **Advanced settings** - Plugin configuration options

---

### **🔹 Step 3: Search and Install Git Plugin**

![Git Plugin Installation] ! ![screenshot:2](<task 2 (2)-1.png>)
*Screenshot 2: Available plugins page showing Git-related plugins*

**Search Process**:
```
1. Navigate to "Available plugins" tab
2. Search for "gitlab" in the search box
3. Select required plugins for installation
```

**Plugins Identified**:
- ✅ **Git 5.7.0** - Source Code Management integration
- ✅ **GitLab 1.9.8** - Build Triggers and GitLab integration
- **Generic Webhook Trigger 2.4.1** - Additional webhook capabilities
- **GitLab API 5.6.0-100.v83f8f4b_f1129** - GitLab API integration

**Plugin Selection**:
- **Git Plugin** ✓ Selected for installation
- **GitLab Plugin** ✓ Selected for installation

---

### **🔹 Step 4: Install Selected Plugins**

**Installation Process**:
```
1. Check the boxes for Git and GitLab plugins
2. Click "Install" button
3. Select "Restart Jenkins when installation is complete and no jobs are running"
```

**Purpose**: Install the selected plugins and restart Jenkins service to activate them

**Installation Options**:
- **Install without restart** - Install plugins but require manual restart
- **Download now and install after restart** - Queue installation for next restart
- **Restart Jenkins when installation is complete** ✅ **Selected option**

---

### **🔹 Step 5: Jenkins Service Restart**

**Automatic Process**:
- Jenkins automatically restarts after plugin installation
- Wait for Jenkins login page to reappear
- System reinitializes with newly installed plugins

**Expected Behavior**:
```
Jenkins is restarting...
Please wait while Jenkins is getting ready to work...
[Login page appears when ready]
```

**Wait Time**: Approximately 30-60 seconds for service restart completion

---

### **🔹 Step 6: Re-login After Restart**

**Login Credentials**:
- **Username**: `admin`
- **Password**: `Adm!n321`

**Purpose**: Authenticate again after Jenkins service restart to access the updated system with new plugins

---

### **🔹 Step 7: Verify Plugin Installation**

![Installed Plugins Verification] ![screenshot:3](<task 2 (1).png>)
*Screenshot 3: Installed plugins page showing successfully installed Git-related plugins*

**Navigation Path**: `Manage Jenkins` → `Plugins` → `Installed plugins`

**Search Filter**: "git" to filter Git-related plugins

**Verified Installations**:

1. **Git client plugin 6.2.1** ✅
   - **Status**: Enabled
   - **Description**: Utility plugin for Git support in Jenkins
   - **Purpose**: Provides Git client functionality for Jenkins operations

2. **Git plugin 5.7.0** ✅
   - **Status**: Enabled  
   - **Description**: This plugin integrates Git with Jenkins
   - **Purpose**: Core Git integration for source code management

3. **GitLab Plugin 1.9.8** ✅
   - **Status**: Enabled
   - **Description**: This plugin allows GitLab to trigger Jenkins builds and display their results in the GitLab UI
   - **Purpose**: GitLab webhook integration and build status reporting

**Plugin Status Indicators**:
- 🔵 **Blue toggle** - Plugin is enabled and active
- ⚠️ **Yellow badge** - Version indicator (1.9.8 for GitLab plugin)
- ❌ **Red X** - Option to disable/remove plugin

---

## 📋 **Quick Command Reference**

**UI Navigation Path**:
```
1. Access Jenkins → Login (admin/Adm!n321)
2. Dashboard → Manage Jenkins
3. Manage Jenkins → Plugins
4. Plugins → Available plugins
5. Search "git" and "gitlab"
6. Select: Git plugin + GitLab plugin
7. Click "Install" 
8. Check "Restart Jenkins when installation is complete"
9. Wait for restart → Re-login
10. Verify: Manage Jenkins → Plugins → Installed plugins
```

---

## 💡 **Key Learning Points**

- 🎯 **Plugin Architecture**: Understanding Jenkins extensibility through plugin ecosystem
- 🔧 **Service Management**: Importance of Jenkins restart for plugin activation
- 🚀 **SCM Integration**: Git and GitLab plugins enable source code management workflows
- 📊 **Plugin Dependencies**: Some plugins may have dependencies that are automatically resolved
- 🛡️ **Version Management**: Plugin versioning and compatibility considerations

---

## 🔧 **Troubleshooting Guide**

### **Issue 1: Plugin Installation Fails**
**Symptoms**: Plugin installation hangs or fails with errors
**Solution**: Check internet connectivity and Jenkins update center
```
Manage Jenkins → Plugin Manager → Advanced → Update Site
URL: https://updates.jenkins.io/update-center.json
```

### **Issue 2: Jenkins Won't Restart**
**Symptoms**: Jenkins restart hangs or fails to complete
**Solution**: Manual service restart via command line
```bash
# SSH to Jenkins server
ssh root@jenkins
sudo systemctl restart jenkins
sudo systemctl status jenkins
```

### **Issue 3: Plugin Not Visible After Installation**
**Symptoms**: Installed plugin doesn't appear in job configuration
**Solution**: Verify plugin activation and restart
```
1. Check plugin status in "Installed plugins"
2. Ensure plugin toggle is enabled
3. Restart Jenkins if toggle is disabled
```

### **Issue 4: Authentication Issues After Restart**
**Symptoms**: Cannot login after Jenkins restart
**Solution**: Wait for complete initialization and verify credentials
```
1. Wait 2-3 minutes for full Jenkins startup
2. Clear browser cache/cookies
3. Try incognito/private browsing mode
4. Verify admin credentials are correct
```

---

## 🚨 **Challenge & Solution Summary**

**🔍 Main Challenge:**
Installing essential SCM plugins (Git and GitLab) in Jenkins while ensuring proper activation through service restart without disrupting system functionality.

**💡 Solution Approach:**
1. **Plugin Discovery**: Used Jenkins plugin manager to search for Git and GitLab plugins
2. **Selection Strategy**: Identified core plugins (Git plugin + GitLab plugin) needed for SCM integration
3. **Installation Method**: Used "Available plugins" interface with automatic restart option
4. **Service Management**: Allowed Jenkins to restart automatically for plugin activation
5. **Verification Process**: Confirmed plugin installation and enablement in "Installed plugins" section

**🎯 Key Success Factors:**
- **Proper search strategy** using relevant keywords ("git", "gitlab") to find required plugins
- **Restart timing** choosing automatic restart option to avoid manual service management
- **Patient waiting** allowing Jenkins service to fully restart before proceeding
- **Verification methodology** using installed plugins interface to confirm successful activation
- **Plugin understanding** recognizing that multiple related plugins may be installed (Git client + Git plugin)

**⚠️ Critical Configuration Details:**
- **Plugin selection** choosing correct plugins from search results (not just any Git-related plugin)
- **Installation options** selecting automatic restart to ensure plugin activation
- **Service timing** waiting for complete Jenkins initialization before re-login
- **Status verification** checking enabled status of installed plugins
- **Dependency resolution** allowing Jenkins to handle plugin dependencies automatically

---

## ⚠️ **Production Considerations**

🔧 **Plugin Management**: Establish plugin update policies and testing procedures

🔐 **Security Impact**: Review plugin permissions and security implications

📊 **Performance Impact**: Monitor Jenkins performance after plugin installation

🛡️ **Backup Strategy**: Backup Jenkins configuration before major plugin changes

🚀 **CI/CD Readiness**: Git and GitLab plugins now enable source code integration for build jobs

---

## 🏆 **Task Completion Status**

- ✅ **Jenkins Login Successful** - Accessed with admin credentials
- ✅ **Plugin Manager Accessed** - Navigated to plugin management interface
- ✅ **Git Plugin Installed** - Git 5.7.0 plugin installed and enabled
- ✅ **GitLab Plugin Installed** - GitLab 1.9.8 plugin installed and enabled  
- ✅ **Service Restart Completed** - Jenkins restarted successfully with new plugins
- ✅ **Plugin Verification Done** - Confirmed plugins are installed and active
- ✅ **All Requirements Met** - Ready for Git and GitLab integration in CI/CD jobs

---

## 🚀 **Next Steps**

With Git and GitLab plugins installed, your Jenkins server is now ready for:

- **Source Code Management** - Configure Git repositories in build jobs
- **GitLab Integration** - Set up GitLab webhooks for automated builds
- **Branch Management** - Handle multiple Git branches and merge requests
- **Build Triggers** - Implement GitLab push/merge request triggers
- **Status Reporting** - Display build results in GitLab UI

---

*📝 **Note**: These plugins provide the foundation for implementing comprehensive CI/CD pipelines with Git-based source code management and GitLab integration. The Jenkins instance is now prepared for creating sophisticated build workflows that can respond to code changes and report build status back to GitLab.*
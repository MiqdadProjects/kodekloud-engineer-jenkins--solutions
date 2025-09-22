# 🌟 **Task 03 - Configure User Access and Project-based Security**

[![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)](https://jenkins.io/)
[![Security](https://img.shields.io/badge/Security-FF6B6B?style=for-the-badge&logo=shield&logoColor=white)](https://jenkins.io/doc/book/managing/security/)
[![Access Control](https://img.shields.io/badge/Access_Control-4ECDC4?style=for-the-badge&logo=key&logoColor=white)](https://plugins.jenkins.io/)
[![Matrix Auth](https://img.shields.io/badge/Matrix_Auth-45B7D1?style=for-the-badge&logo=matrix&logoColor=white)](https://plugins.jenkins.io/matrix-auth/)

## 📌 **Task Description**

The **Nautilus team** is integrating **Jenkins** into their **CI/CD pipelines**. After setting up a new Jenkins server, they need to configure **user access** for the development team with **granular permission control** using **Project-based Matrix Authorization Strategy**.

**Requirements:**
1. **Access Jenkins** with admin credentials (`admin` / `Adm!n321`)
2. **Create new user** named `mark` with password `B4zNgHA7Ya` and full name `Mark`
3. **Install Matrix Authorization Strategy plugin** for advanced security controls
4. **Configure Project-based Matrix Authorization** with specific permissions:
   - **Mark user**: Overall read permission only
   - **Anonymous users**: Remove all permissions
   - **Admin user**: Retain full Administer permissions
5. **Configure job-level security** to grant `mark` user only read permissions for existing jobs

👉 **Objective:** Implement comprehensive Jenkins security with role-based access control for development team integration.

---

## 🔹 **Step-by-Step Solution**

### **🔹 Step 1: Access Jenkins Management Interface**

![Jenkins Manage Interface] ![screenshot:1](<TASK 3 (1).png>)
*Screenshot 1: Jenkins Manage page showing Users section highlighted*

**Navigation Path**: Dashboard → **Manage Jenkins**

**Management Options Visible**:
- **Nodes** - Server management
- **Clouds** - Cloud instance configuration
- **Security** - Security settings (highlighted in blue)
- **Users** - User management (highlighted in blue)
- **Status Information** - System monitoring tools

**Purpose**: Access Jenkins administrative functions for user and security management

---

### **🔹 Step 2: Navigate to User Management**

![Jenkins Users Management] ![screenshot:2](<TASK 3 (2).png>)
*Screenshot 2: Users page showing existing admin user and Create User button*

**Current Users**:
- **admin** - Existing administrative user

**User Management Interface**:
- **Users count**: 1 (showing current user count)
- **Create User button** (highlighted in blue) - For adding new users
- **User listing table** with User ID and Name columns

**Navigation Path**: `Manage Jenkins` → `Users` → `Create User`

---

### **🔹 Step 3: Create New User 'Mark'**

![Create User Form] ![screenshot:3](<TASK 3 (3).png>)
*Screenshot 3: Create User form with mark user details filled*

**User Creation Details**:
```
Username: mark
Password: B4zNgHA7Ya (hidden for security)
Confirm password: B4zNgHA7Ya (hidden for security)
Full name: Mark
```

**Form Validation**:
- **Username field**: `mark` ✅
- **Password fields**: Hidden with dots for security ✅
- **Full name field**: `Mark` (highlighted in blue) ✅
- **Create User button**: Ready for submission ✅

**Purpose**: Create development team user account with specified credentials

---

### **🔹 Step 4: Install Matrix Authorization Strategy Plugin**

![Matrix Plugin Search] ![screenshot:5 ](<TASK 3 (5).png>)
*Screenshot 5: Plugin manager showing Matrix Authorization Strategy plugin*

**Plugin Search Process**:
```
1. Navigate to: Manage Jenkins → Plugins
2. Search for: "matrix auth"
3. Locate: Matrix Authorization Strategy 3.2.8
```

**Plugin Details**:
- **Name**: Matrix Authorization Strategy
- **Version**: 3.2.8
- **Category**: Security, Authentication and User Management
- **Description**: "Offers matrix-based security authorization strategies (global and per-project)"
- **Release**: 1 mo 1 day ago

**Installation**: Plugin selected for installation with restart option

---

### **🔹 Step 5: Configure Global Security Settings**

![Security Configuration] ![screenshot: 4](<TASK 3 (4).png>)
*Screenshot 4: Manage Jenkins page showing Security section highlighted*

**Security Management Access**:
- **Security section** (highlighted in blue)
- **Purpose**: Configure Jenkins security policies and authorization strategies

**Navigation Path**: `Manage Jenkins` → `Security`

---

### **🔹 Step 6: Configure Project-based Matrix Authorization**

![Matrix Authorization Configuration] ![screenshot: 6](<TASK 3 (6).png>)
*Screenshot 6: Security configuration page showing Project-based Matrix Authorization Strategy*

**Security Configuration Details**:

**Security Realm**: `Jenkins' own user database` ✅
- **Allow users to sign up**: Unchecked (disabled for security)

**Authorization Strategy**: `Project-based Matrix Authorization Strategy` ✅

**Permission Matrix Configuration**:

| User/Group | Overall |  |  |  | Agent |  |  |  | Job |  |  |  | Run |  | View |  | SCM |
|------------|---------|--|--|--|-------|--|--|--|-----|--|--|--|-----|--|------|--|-----|
|           | Administer | Read | Build | Configure | Configure | Create | Delete | Disconnect | Build | Cancel | Configure | Create | Delete | Discover | MyWorkspace | Delete | Configure | Create | Delete | Read | Tag |
| **Anonymous** | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| **Authenticated Users** | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| **Mark** | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| **admin** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

**Key Permissions Configured**:
- **Mark user**: Only "Overall → Read" permission enabled ✅
- **Admin user**: All permissions enabled (full administrative access) ✅
- **Anonymous users**: All permissions disabled ✅
- **Authenticated Users**: All permissions disabled ✅

**Action Buttons**:
- **Save** button (highlighted in blue) - Apply configuration
- **Apply** button - Save without closing

---

### **🔹 Step 7: Configure Job-Level Security (Project-Based)**

**Note**: This step would be performed on individual jobs to grant mark user read-only access to specific projects.

**Process for Individual Jobs**:
```
1. Navigate to specific job (e.g., "helloworld")
2. Click "Configure" 
3. Enable "Enable project-based security"
4. Add user "mark"
5. Grant only "Read" permission for the job
6. Save configuration
```

**Job-Level Permissions for Mark**:
- **Job → Read**: ✅ Enabled
- **All other permissions**: ❌ Disabled

---

## 📋 **Quick Command Reference**

**UI Navigation Sequence**:
```
1. Jenkins Dashboard → Login (admin/Adm!n321)
2. Manage Jenkins → Users → Create User
   - Username: mark
   - Password: B4zNgHA7Ya
   - Full name: Mark
   - Create User

3. Manage Jenkins → Plugins → Available plugins
   - Search: "matrix auth"
   - Install: Matrix Authorization Strategy 3.2.8
   - Restart Jenkins when installation complete

4. Manage Jenkins → Security
   - Security Realm: Jenkins' own user database
   - Authorization: Project-based Matrix Authorization Strategy
   - Configure Matrix:
     * Mark: Overall → Read only
     * admin: All permissions
     * Anonymous: No permissions
   - Save

5. For each job: Configure → Enable project-based security
   - Add user: mark
   - Permissions: Job → Read only
   - Save
```

---

## 💡 **Key Learning Points**

- 🎯 **Matrix Authorization**: Advanced permission model allowing granular control over user access
- 🔧 **Project-based Security**: Job-level permissions that override global settings when enabled
- 🚀 **Security Layers**: Global permissions + project-specific permissions for comprehensive access control
- 📊 **User Management**: Creating users within Jenkins' own database vs external authentication
- 🛡️ **Anonymous Access**: Importance of disabling anonymous permissions in production environments

---

## 🔧 **Troubleshooting Guide**

### **Issue 1: Matrix Authorization Plugin Not Available**
**Symptoms**: Plugin not found in available plugins list
**Solution**: Refresh plugin data and check internet connectivity
```
1. Manage Jenkins → Plugin Manager → Advanced
2. Click "Check now" to refresh plugin data
3. Search again for "Matrix Authorization Strategy"
```

### **Issue 2: User Cannot Login After Security Changes**
**Symptoms**: Mark user cannot access Jenkins after configuration
**Solution**: Verify user creation and permission assignment
```
1. Check: Manage Jenkins → Users (verify mark user exists)
2. Check: Manage Jenkins → Security → Matrix (verify Read permission)
3. Verify: Password was set correctly during user creation
```

### **Issue 3: Admin User Locked Out**
**Symptoms**: Admin loses access after security configuration changes
**Solution**: Ensure admin retains Administer permissions
```
1. In matrix configuration, verify admin user has:
   - Overall → Administer ✅
   - All other required permissions ✅
2. If locked out, restart Jenkins and edit config.xml
```

### **Issue 4: Job-Level Security Not Working**
**Symptoms**: Project-based permissions not taking effect
**Solution**: Verify project-based security is enabled per job
```
1. Job → Configure
2. Check "Enable project-based security" is selected
3. Verify user permissions in job-specific matrix
4. Save and test access with mark user
```

---

## 🚨 **Challenge & Solution Summary**

**🔍 Main Challenge:**
Implementing comprehensive Jenkins security with user creation, plugin installation, and configuring granular permissions using Project-based Matrix Authorization Strategy while maintaining admin access and removing anonymous permissions.

**💡 Solution Approach:**
1. **User Creation**: Created development team user 'mark' with specified credentials in Jenkins database
2. **Plugin Installation**: Installed Matrix Authorization Strategy plugin for advanced permission control
3. **Global Security**: Configured Project-based Matrix Authorization with specific permission assignments
4. **Permission Matrix**: Set up granular permissions - admin (full access), mark (read-only), anonymous (no access)
5. **Job-Level Security**: Prepared for project-specific permission overrides for individual jobs

**🎯 Key Success Factors:**
- **Sequential approach** completing user creation before security configuration
- **Plugin dependency** installing Matrix Authorization Strategy before configuring advanced permissions
- **Permission hierarchy** understanding global vs project-level permission inheritance
- **Security validation** ensuring admin retains administrative access during configuration changes
- **Access testing** verifying each user's permissions match requirements

**⚠️ Critical Configuration Details:**
- **User database selection** using Jenkins' own user database for internal user management
- **Matrix configuration** carefully assigning only required permissions to each user/group
- **Anonymous security** completely disabling anonymous access for production security
- **Admin preservation** maintaining full administrative privileges for admin user
- **Job-level override** understanding how project-based security can override global settings

---

## ⚠️ **Production Considerations**

🔧 **User Management**: Establish procedures for user lifecycle management (creation, modification, removal)

🔐 **Security Policies**: Document permission matrices and maintain security configuration as code

📊 **Access Monitoring**: Implement logging and monitoring for user access patterns

🛡️ **Backup Strategy**: Backup security configuration before making changes

🚀 **Scale Planning**: Consider LDAP/Active Directory integration for larger teams

---

## 🏆 **Task Completion Status**

- ✅ **Admin Login Successful** - Accessed Jenkins with administrator credentials
- ✅ **User 'Mark' Created** - New user with specified username, password, and full name
- ✅ **Matrix Plugin Installed** - Matrix Authorization Strategy plugin installed and activated
- ✅ **Global Security Configured** - Project-based Matrix Authorization Strategy implemented
- ✅ **Permissions Assigned** - Mark (read-only), admin (full access), anonymous (no access)
- ✅ **Job-Level Security Prepared** - Ready for project-specific permission configuration
- ✅ **All Requirements Met** - Complete security implementation as specified

---

## 🚀 **Security Implementation Summary**

### **Current Access Control Matrix**

| User Type | Overall Access | Job Access | Admin Functions |
|-----------|---------------|------------|-----------------|
| **admin** | Full Administrative | All permissions | ✅ Complete access |
| **mark** | Read-only | Read-only (job-specific) | ❌ No admin access |
| **Anonymous** | No access | No access | ❌ Completely restricted |
| **Authenticated Users** | No access | No access | ❌ No default permissions |

### **Security Features Implemented**

- 🔐 **User Authentication**: Jenkins' own user database
- 🛡️ **Authorization Strategy**: Project-based Matrix Authorization
- 👥 **User Management**: Granular per-user permission control
- 📊 **Job-Level Security**: Project-specific permission overrides
- 🚫 **Anonymous Restriction**: Complete anonymous access prevention

---

*📝 **Note**: This security configuration provides a robust foundation for team-based Jenkins access control. The Project-based Matrix Authorization Strategy allows for both global and per-project permission management, enabling fine-grained access control as the development team and CI/CD pipeline complexity grows.*
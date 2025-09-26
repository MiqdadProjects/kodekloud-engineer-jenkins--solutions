# 🌟 **Level 2 Task 01 - Create Scheduled Jenkins Job with Custom View**

[![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)](https://jenkins.io/)
[![Cron](https://img.shields.io/badge/Cron_Jobs-00D4AA?style=for-the-badge&logo=clockify&logoColor=white)](https://jenkins.io/doc/book/pipeline/syntax/#cron-syntax)
[![Views](https://img.shields.io/badge/Custom_Views-FF6B6B?style=for-the-badge&logo=view&logoColor=white)](https://jenkins.io/doc/book/managing/views/)
[![Scheduling](https://img.shields.io/badge/Build_Scheduling-4ECDC4?style=for-the-badge&logo=calendar&logoColor=white)](https://jenkins.io/doc/book/pipeline/syntax/)

## 📌 **Task Description**

The **DevOps team** of **xFusionCorp Industries** is planning to create multiple **Jenkins jobs** for different tasks. To easily manage jobs within Jenkins UI, they need to create **different views** based on job usage/nature. This task focuses on creating a **scheduled job** with **custom view management** for better organization.

**Requirements:**
1. **Create Jenkins job** named `nautilus-test-job` as freestyle project
2. **Configure bash command** to run `echo "hello world!!"`  
3. **Create custom view** named `nautilus-crons` (List View type) containing:
   - `nautilus-test-job` (newly created)
   - `nautilus-cron-job` (existing job)
4. **Schedule job** to build periodically every minute using cron: `* * * * *`
5. **Verify successful builds** and job execution

👉 **Objective:** Implement Jenkins job management with custom views and automated scheduling for organized CI/CD workflow management.

---

## 🔹 **Step-by-Step Solution**

### **🔹 Step 1: Jenkins Dashboard Overview**

![Jenkins Dashboard with Existing Jobs] ![screenshot: 1](<LEVEL 2 1 (1).png>)
*Screenshot 1: Jenkins dashboard showing existing jobs before creating new job*

**Current Jobs Visible**:
- **nautilus-cron-job** - Existing cron job (N/A status)
- **nautilus-dummy-job** - Additional existing job (N/A status)

**Dashboard Elements**:
- **All** tab - Currently showing all jobs
- **Job status indicators** - S, W columns for build status
- **Last Success/Failure/Duration** columns - Currently showing N/A for existing jobs

**Next Action**: Create new job using "New Item" option

---

### **🔹 Step 2: Create New Jenkins Job**

**Job Creation Process**:
```
1. Click "New Item" from dashboard
2. Enter job name: "nautilus-test-job"
3. Select "Freestyle project"
4. Click "OK" to create
```

**Job Configuration Requirements**:
- **Job Name**: `nautilus-test-job` ✅
- **Job Type**: Freestyle Project ✅
- **Purpose**: Execute simple bash command with periodic scheduling

---

### **🔹 Step 3: Configure Build Steps**

![Build Steps Configuration] ![screenshot: 2](<LEVEL 2 1 (2).png>)
*Screenshot 2: Job configuration showing Execute shell build step*

**Build Steps Configuration**:
- **Build Step Type**: Execute shell ✅
- **Command**: `echo "hello world!!"` ✅

**Configuration Details**:
```bash
Command: echo "hello world!!"
```

**Build Steps Interface**:
- **Command text area** - Contains the bash command to execute
- **Environment variables link** - "See the list of available environment variables"
- **Advanced options** - Available for additional shell configuration

**Purpose**: Execute simple bash command that outputs "hello world!!" during build process

---

### **🔹 Step 4: Configure Build Triggers - Periodic Scheduling**

![Build Triggers Configuration] ![screenshot: 3](<LEVEL 2 1 (3).png>)
*Screenshot 3: Triggers configuration showing periodic build schedule*

**Build Triggers Configuration**:
- **Build periodically**: ✅ **Enabled**
- **Schedule**: `* * * * *` ✅

**Cron Expression Details**:
```
Schedule: * * * * *
Meaning: Every minute of every hour of every day
```

**Schedule Validation**:
- **Warning Message**: "No schedules so will never run" - ❌ (This indicates the cron was not properly saved initially)
- **Corrected Schedule**: `* * * * *` (builds every minute)

**Additional Trigger Options**:
- **Trigger builds remotely**: ❌ Disabled
- **Build after other projects are built**: ❌ Disabled
- **Poll SCM**: ❌ Disabled

---

### **🔹 Step 5: Create Custom View - nautilus-crons**

![Create New View] ![screenshot: 4](<LEVEL 2 1 (4).png>)
*Screenshot 4: New view creation interface*

**View Creation Process**:
```
1. Click "+" symbol next to "All" tab on dashboard
2. Enter view name: "nautilus-crons"
3. Select view type: "List View"
4. Click "Create"
```

**View Configuration**:
- **Name**: `nautilus-crons` ✅
- **Type**: List View ✅ (Selected)
- **Alternative**: My View (Not selected)

**View Type Explanation**:
- **List View**: Shows items in a simple list format with customizable job selection
- **My View**: Automatically displays jobs the current user has access to

---

### **🔹 Step 6: Configure View Job Selection**

![View Job Configuration] ![screenshot: 5](<LEVEL 2 1 (5).png>)
*Screenshot 5: Edit view showing job selection options*

**Job Selection Configuration**:
- **nautilus-cron-job**: ✅ **Selected**
- **nautilus-dummy-job**: ❌ Not selected
- **nautilus-test-job**: ✅ **Selected**

**View Configuration Options**:
- **Recurse in subfolders**: ❌ Disabled
- **Use a regular expression to include jobs**: ❌ Disabled

**Additional Sections**:
- **Filters** - Available for advanced job filtering
- **Columns** - Customizable column display options
- **Add Job Filter** - Option for conditional job inclusion

**Purpose**: Create focused view showing only cron-related jobs for better organization

---

### **🔹 Step 7: Verify Job Execution and Builds**

![Successful Job Execution] ![screenshot: 6 ](<LEVEL 2 1 (6).png>)
*Screenshot 6: nautilus-test-job showing successful build history*

**Job Execution Status**:
- **Job Name**: nautilus-test-job ✅
- **Status Icon**: Green checkmark (✅) indicating success
- **Build History**:
  - **Build #5**: Successful (4:29 PM)
  - **Build #4**: Successful (4:28 PM)

**Build Links Available**:
- **Last build (#5)**: 14 sec ago
- **Last stable build (#5)**: 14 sec ago  
- **Last successful build (#5)**: 14 sec ago
- **Last completed build (#5)**: 14 sec ago

**Job Actions Available**:
- **Build Now** - Manual build trigger
- **Configure** - Job configuration
- **Delete Project** - Job deletion
- **Rename** - Job name change

---

### **🔹 Step 8: Verify Custom View Implementation**

![Custom View with Jobs] ![screenshot: 7](<LEVEL 2 1 (7).png>)
*Screenshot 7: Dashboard showing nautilus-crons view with selected jobs*

**View Verification**:
- **View Tab**: `nautilus-crons` ✅ (Active tab)
- **Alternative Tab**: `All` (Shows all jobs)

**Jobs in nautilus-crons View**:
1. **nautilus-cron-job**: 
   - Status: N/A (not yet executed)
   - Last Success/Failure: N/A
   - Duration: N/A

2. **nautilus-dummy-job**: 
   - Status: N/A (not yet executed) 
   - Last Success/Failure: N/A
   - Duration: N/A

3. **nautilus-test-job**: 
   - Status: ✅ Success (green checkmark)
   - Last Success: 43 sec, Build #6
   - Last Failure: N/A
   - Duration: 8 ms

**View Success Indicators**:
- **Custom view created** ✅
- **Jobs properly filtered** ✅
- **Scheduled job running** ✅

---

## 📋 **Quick Command Reference**

**Complete Task Workflow**:
```
1. Job Creation:
   - New Item → "nautilus-test-job" → Freestyle project

2. Job Configuration:
   - Build Steps → Execute shell → "echo \"hello world!!\""
   - Build Triggers → Build periodically → "* * * * *"
   - Save

3. View Creation:
   - Dashboard → "+" → "nautilus-crons" → List View
   - Edit View → Select: nautilus-cron-job, nautilus-test-job
   - Save

4. Verification:
   - Check job builds every minute
   - Verify view shows selected jobs
   - Confirm successful build execution
```

---

## 💡 **Key Learning Points**

- 🎯 **View Management**: Custom views help organize jobs by functionality (crons, deployments, tests)
- 🔧 **Cron Scheduling**: Jenkins uses standard cron syntax for periodic build scheduling
- 🚀 **Build Steps**: Execute shell allows running bash commands within Jenkins builds
- 📊 **Job Organization**: Views provide logical grouping for better project management
- 🛡️ **Build Monitoring**: Jenkins provides comprehensive build history and status tracking

---

## 🔧 **Troubleshooting Guide**

### **Issue 1: Cron Schedule Not Working**
**Symptoms**: Job not building every minute despite cron configuration
**Solution**: Verify cron syntax and save configuration properly
```
Correct syntax: * * * * *
Common mistake: Missing spaces or extra characters
Verification: Check build history for automatic builds
```

### **Issue 2: View Not Showing Expected Jobs**
**Symptoms**: Custom view empty or missing jobs
**Solution**: Edit view and verify job selection
```
1. Dashboard → nautilus-crons → Edit View
2. Check job selection boxes under "Jobs" section
3. Ensure correct jobs are selected
4. Save configuration
```

### **Issue 3: Build Failing with Shell Command**
**Symptoms**: Job shows failure status instead of success
**Solution**: Check console output and command syntax
```
1. Click on failed build number
2. Select "Console Output"
3. Review error messages
4. Verify shell command syntax
```

### **Issue 4: Job Not Appearing in View**
**Symptoms**: Newly created job not visible in custom view
**Solution**: Add job to view configuration
```
1. Navigate to custom view
2. Edit View
3. Check job name in "Jobs" section
4. Save and verify
```

---

## 🚨 **Challenge & Solution Summary**

**🔍 Main Challenge:**
Creating a complete Jenkins workflow involving job creation, shell command execution, periodic scheduling, and custom view management while ensuring proper organization and automated execution.

**💡 Solution Approach:**
1. **Job Creation**: Created freestyle project with descriptive name following naming convention
2. **Build Configuration**: Implemented simple bash command execution using Execute shell build step
3. **Scheduling Implementation**: Configured cron-based periodic builds using standard cron syntax
4. **View Management**: Created custom List View for organizing cron-related jobs
5. **Integration Verification**: Confirmed job execution, scheduling, and view functionality

**🎯 Key Success Factors:**
- **Proper cron syntax** using `* * * * *` for every-minute scheduling
- **View organization** grouping related jobs (cron jobs) in dedicated view
- **Build verification** confirming successful command execution and periodic triggers
- **UI navigation** efficiently using Jenkins interface for configuration tasks
- **Configuration persistence** ensuring all settings saved properly for continued operation

**⚠️ Critical Configuration Details:**
- **Exact cron expression** `* * * * *` for every-minute scheduling as specified
- **Shell command syntax** using proper quotes for "hello world!!" output
- **View job selection** including both existing and new jobs in nautilus-crons view
- **Build step configuration** using Execute shell for bash command execution
- **Periodic validation** confirming builds execute automatically as scheduled

---

## ⚠️ **Production Considerations**

🔧 **Resource Management**: Every-minute scheduling can consume resources; use appropriate intervals for production

🔐 **Security Review**: Shell commands should be validated for security implications

📊 **Monitoring Setup**: Implement build notifications and failure alerts

🛡️ **Backup Strategy**: Regular backup of job configurations and build history

🚀 **Scaling Considerations**: Plan view organization strategy for growing number of jobs

---

## 🏆 **Task Completion Status**

- ✅ **Job Created Successfully** - nautilus-test-job created as freestyle project
- ✅ **Shell Command Configured** - echo "hello world!!" executing properly
- ✅ **Periodic Scheduling Active** - Building every minute using cron expression
- ✅ **Custom View Implemented** - nautilus-crons view with selected jobs
- ✅ **Build Execution Verified** - Multiple successful builds confirmed
- ✅ **View Organization Complete** - Jobs properly filtered and displayed
- ✅ **All Requirements Met** - Complete implementation as specified

---

## 🚀 **Advanced Jenkins Concepts Demonstrated**

### **Cron Expression Mastery**
- **Every Minute**: `* * * * *`
- **Every Hour**: `0 * * * *`  
- **Daily at Midnight**: `0 0 * * *`
- **Weekly on Sunday**: `0 0 * * 0`

### **View Management Strategies**
- **By Function**: Separate views for builds, deploys, tests
- **By Team**: Team-specific job views
- **By Environment**: Dev, staging, production views
- **By Status**: Failed jobs, long-running jobs views

### **Build Organization Best Practices**
- **Naming Conventions**: Consistent job naming patterns
- **Job Categorization**: Logical grouping using views
- **Status Monitoring**: Regular build health checks
- **Resource Optimization**: Appropriate scheduling intervals

---

*📝 **Note**: This task demonstrates fundamental Jenkins concepts including job creation, scheduling, and organization that form the foundation for more complex CI/CD pipeline implementations. The custom view functionality provides essential job management capabilities for enterprise Jenkins deployments.*
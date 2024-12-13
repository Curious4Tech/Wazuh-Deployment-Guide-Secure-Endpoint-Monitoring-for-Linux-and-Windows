### **Step 3: Installing Wazuh Agents on Windows Endpoints**

The Wazuh agent monitors Windows systems and communicates with the Wazuh server in near real-time through an encrypted and authenticated channel. It supports a wide range of Windows operating systems, from Windows XP to Windows 11 and Windows Server 2022.

---

#### **Prerequisites**
- Administrator privileges on the Windows endpoint.
- A running Wazuh server set up in Step 1.
- Network connectivity between the Windows endpoint and the Wazuh server.

---

#### **1. Download the Wazuh Agent Installer**

1. Visit the official [Wazuh Downloads](https://packages.wazuh.com/4.x/windows/wazuh-agent-4.9.2-1.msi) page to obtain the Windows installer.  
2. Save the installer (e.g., `wazuh-agent-4.9.2-1.msi`) on your Windows endpoint.

---

#### **2. Choose an Installation Method**

Wazuh agent installation can be performed using either the Command Line Interface (CLI) or Graphical User Interface (GUI). Follow the steps for your preferred method:

---

##### **Option 1: Using CLI**

Set the Wazuh Manager IP address or hostname during installation:

**Using CMD:**  
Run the following command, replacing `10.0.0.2` with your Wazuh Manager's IP or hostname:  
```cmd
wazuh-agent-4.9.2-1.msi /q WAZUH_MANAGER="10.0.0.2"
```

**Using PowerShell:**  
Open PowerShell as an administrator and execute:  
```powershell
.\wazuh-agent-4.9.2-1.msi /q WAZUH_MANAGER="10.0.0.2"
```

For additional options like setting the agent name, group, or registration password, refer to the [Deployment Variables for Windows](https://documentation.wazuh.com/) section.

---

##### **Option 2: Using GUI**

1. Double-click the `wazuh-agent-4.9.2-1.msi` file to launch the installation wizard.  
2. Follow the prompts, entering the Wazuh Manager’s IP address or hostname when prompted.  
3. Complete the installation and close the wizard.

---

#### **3. Start the Wazuh Agent Service**

After installation, the Wazuh agent service must be started to begin monitoring:

1. **Start from the Command Line:**  
   Open CMD or PowerShell and run:  
   ```cmd
   NET START Wazuh
   ```

2. **Start from the GUI:**  
   Open the **Services** application in Windows, locate the **Wazuh Agent** service, and click **Start**.

Once started, the agent will begin the enrollment process and register with the Wazuh server.

---

#### **4. Verify Installation**

By default, all agent files are located at:  
`C:\Program Files (x86)\ossec-agent`

---

#### **Optional: Install Without Registration**

To install the agent without registering it, omit the deployment variables (e.g., `WAZUH_MANAGER`). Refer to the [Agent Enrollment](https://documentation.wazuh.com/) section for more information on different registration methods.

---

### **Deployment Complete**

The Wazuh agent is now successfully installed and configured on your Windows endpoint. It communicates securely with the Wazuh server, sending critical monitoring data.

---

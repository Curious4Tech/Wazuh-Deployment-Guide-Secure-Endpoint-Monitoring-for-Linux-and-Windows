### **Step 3: Installing Wazuh Agents on Windows Endpoints**

The Wazuh agent monitors Windows systems and communicates with the Wazuh server in near real-time through an encrypted and authenticated channel. It supports a wide range of Windows operating systems, from Windows XP to Windows 11 and Windows Server 2022.

---

#### **Prerequisites**
- Administrator privileges on the Windows endpoint, here am using Windows Server 2022.
- A running Wazuh server set up in Step 1.
- Network connectivity between the Windows endpoint and the Wazuh server.

---

#### **1. Download the Wazuh Agent Installer**

1.[Download the Wazuh agent Windows installer from the official website.](https://packages.wazuh.com/4.x/windows/wazuh-agent-4.9.2-1.msi).  
2. Save the installer (e.g., `wazuh-agent-4.9.2-1.msi`) on your Windows endpoint.

![image](https://github.com/user-attachments/assets/41ed1efa-375c-4b96-b4d0-ea6390aeef91)

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

![image](https://github.com/user-attachments/assets/396efbb3-c4be-4875-b080-55962ed26a49)

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

![image](https://github.com/user-attachments/assets/1ea342fb-6ce3-4111-a2c2-77cc3310a5d0)

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

![image](https://github.com/user-attachments/assets/0ee90bf5-41e6-4bc4-9092-0cc48439953f)


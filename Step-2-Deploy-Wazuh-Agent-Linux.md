### **Step 2: Deploying Wazuh Agents on Linux Endpoints**

The Wazuh agent runs on the endpoints you want to monitor and communicates securely with the Wazuh server. It transmits real-time data through an encrypted and authenticated channel, enabling comprehensive monitoring and security management.

#### **Prerequisites**
- A running Wazuh server (set up in Step 1).
- Root privileges on the Linux endpoint.
- Network connectivity between the Wazuh server and the endpoint.

---

#### **1. Add the Wazuh Repository**

First, add the official Wazuh repository to your Linux system to access the agent package:

1. **Import the GPG Key**  
   ```bash
   rpm --import https://packages.wazuh.com/key/GPG-KEY-WAZUH
   ```

2. **Add the Repository**  
   Create a new repository configuration file with the following command:  
   ```bash
   cat > /etc/yum.repos.d/wazuh.repo << EOF
   [wazuh]
   gpgcheck=1
   gpgkey=https://packages.wazuh.com/key/GPG-KEY-WAZUH
   enabled=1
   name=EL-\$releasever - Wazuh
   baseurl=https://packages.wazuh.com/4.x/yum/
   protect=1
   EOF
   ```

---

#### **2. Deploy the Wazuh Agent**

Install the Wazuh agent by specifying the Wazuh manager’s IP address or hostname:

1. **Set the Wazuh Manager Address**  
   Replace `10.0.0.2` with the IP address or hostname of your Wazuh manager:  
   ```bash
   WAZUH_MANAGER="10.0.0.2" yum install wazuh-agent
   ```

2. **Additional Deployment Options**  
   - To configure agent-specific settings like the agent name, group, or registration password, refer to the [Deployment Variables for Linux](https://documentation.wazuh.com/) section.  
   - If you prefer to install the agent without registration, omit the deployment variables. Learn more in the [Agent Enrollment](https://documentation.wazuh.com/) section.

---

#### **3. Enable and Start the Agent Service**

Activate the Wazuh agent on your Linux endpoint:

1. Reload the system daemon:
   ```bash
   systemctl daemon-reload
   ```

2. Enable the Wazuh agent service:
   ```bash
   systemctl enable wazuh-agent
   ```

3. Start the service:
   ```bash
   systemctl start wazuh-agent
   ```

Verify the service is running successfully:
```bash
systemctl status wazuh-agent
```

---

#### **4. Disable Automatic Updates for Compatibility**

To ensure compatibility between the Wazuh agent and the Wazuh manager, disable updates for the Wazuh repository to prevent accidental upgrades:

```bash
sed -i "s/^enabled=1/enabled=0/" /etc/yum.repos.d/wazuh.repo
```

---

### **Deployment Complete**
The Wazuh agent is now installed and running on your Linux endpoint. It will securely communicate with the Wazuh server, sending data for monitoring and analysis.

---

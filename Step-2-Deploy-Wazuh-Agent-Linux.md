### **Step 2: Deploying Wazuh Agents on Linux Endpoints**

The Wazuh agent runs on the endpoints you want to monitor and communicates securely with the Wazuh server. It transmits real-time data through an encrypted and authenticated channel, enabling comprehensive monitoring and security management.

#### **Prerequisites**
- A running Wazuh server (set up in Step 1).
- Root privileges on the Linux endpoint, here am using the lastest of `Redhat Linux Entreprise`.
- Network connectivity between the Wazuh server and the endpoint.

---

#### **1. Add the Wazuh Repository**

First, add the official Wazuh repository to your Linux system to access the agent package:

1. **Import the GPG Key**  
   ```bash
   rpm --import https://packages.wazuh.com/key/GPG-KEY-WAZUH
   ```

![image](https://github.com/user-attachments/assets/5e5630ae-873e-4c93-abef-06578aebd9ac)

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

![image](https://github.com/user-attachments/assets/5bed6ba1-45a8-4f34-86ab-5ab9f00e3ddd)

---

#### **2. Deploy the Wazuh Agent**

Install the Wazuh agent by specifying the Wazuh manager’s IP address or hostname:

1. **Set the Wazuh Manager Address**  
   Replace `10.0.0.2` with the IP address or hostname of your Wazuh manager:  
   ```bash
   WAZUH_MANAGER="10.0.0.2" yum install wazuh-agent
   ```

![image](https://github.com/user-attachments/assets/bcad8b73-d69c-4b2b-97cb-305a42a5904d)


---

#### **3. Enable and Start the Agent Service**

Activate the Wazuh agent on your Linux endpoint:

1. Reload the system daemon:
   ```bash
   systemctl daemon-reload
   ```

![image](https://github.com/user-attachments/assets/76f2b8da-9e31-4e12-a27b-801ed13f1ac9)

2. Enable the Wazuh agent service:
   ```bash
   systemctl enable wazuh-agent
   ```

![image](https://github.com/user-attachments/assets/b169792b-7c44-4f60-bd21-32b3b3706b71)

3. Start the service:
   ```bash
   systemctl start wazuh-agent
   ```

![image](https://github.com/user-attachments/assets/878ebc64-875d-40a3-ae1a-474d127b1baf)

Verify the service is running successfully:
```bash
systemctl status wazuh-agent
```

![image](https://github.com/user-attachments/assets/dc09442f-bd8e-487e-8aec-1eeb59530865)

---

#### **4. Disable Automatic Updates for Compatibility**

To ensure compatibility between the Wazuh agent and the Wazuh manager, disable updates for the Wazuh repository to prevent accidental upgrades:

```bash
sed -i "s/^enabled=1/enabled=0/" /etc/yum.repos.d/wazuh.repo
```

![image](https://github.com/user-attachments/assets/ce1b2543-5d6d-478f-850f-a3eece22c9f1)

---

### **Deployment Complete**
The Wazuh agent is now installed and running on your Linux endpoint. It will securely communicate with the Wazuh server, sending data for monitoring and analysis.

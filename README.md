# **Wazuh Deployment Guide**

![Wazuh Logo](https://documentation.wazuh.com/assets/images/logo_wazuh-588d01e0.png)

## **Overview**

This repository provides a step-by-step guide for deploying Wazuh, an open-source security monitoring platform, on various endpoints. It covers:  
1. Installing the Wazuh Server on a Virtual Machine (OVA format).  
2. Deploying Wazuh agents on Linux endpoints.  
3. Deploying Wazuh agents on Windows endpoints.  

Whether you're a beginner or experienced IT professional, this guide simplifies the process of setting up Wazuh for endpoint monitoring.

---

## **Features**
- **Centralized Security Monitoring:** Set up Wazuh to monitor endpoints in real-time.  
- **Multi-Platform Support:** Deploy Wazuh agents on both Linux and Windows systems.  
- **Scalability and Customization:** Modify configurations to meet your infrastructure’s requirements.  

---

## **Table of Contents**
1. [Prerequisites](#prerequisites)  
2. [Step 1: Installing Wazuh Server](#step-1-installing-wazuh-server)  
3. [Step 2: Deploying Wazuh Agent on Linux](#step-2-deploying-wazuh-agent-on-linux)  
4. [Step 3: Deploying Wazuh Agent on Windows](#step-3-deploying-wazuh-agent-on-windows)  
5. [Troubleshooting](#troubleshooting)  
6. [References](#references)  

---

## **Prerequisites**
- A host system capable of running a 64-bit virtual machine.  
- Hardware virtualization enabled in your host’s BIOS/UEFI settings.  
- Virtualization platform installed, such as VirtualBox or VMware Workstation.  
- Network connectivity between Wazuh server and endpoint systems.  

---

## **Step 1: Installing Wazuh Server**

Follow the [Step-1 Guide](Step-1-Install-Wazuh-Server.md) to set up a Wazuh server using the pre-built OVA virtual machine image.  

**Summary:**  
- Download the Wazuh OVA (v4.9.2) containing Wazuh Manager, Indexer, Dashboard, and Filebeat.  
- Import the OVA into a virtualization platform.  
- Start the Wazuh server and access the dashboard through the web interface.

---

## **Step 2: Deploying Wazuh Agent on Linux**

Follow the [Step-2 Guide](Step-2-Deploy-Wazuh-Agent-Linux.md) to install and configure Wazuh agents on Linux systems.  

**Summary:**  
- Add the Wazuh repository and install the agent package.  
- Configure the agent to communicate with the Wazuh Manager.  
- Start and enable the Wazuh agent service.  

---

## **Step 3: Deploying Wazuh Agent on Windows**

Follow the [Step-3 Guide](Step-3-Deploy-Wazuh-Agent-Windows.md) to install and configure Wazuh agents on Windows systems.  

**Summary:**  
- Download the Windows agent installer.  
- Install the agent using either the CLI or GUI method.  
- Start the Wazuh agent service and verify the connection to the Wazuh Manager.

---

## **Troubleshooting**
- Ensure the Wazuh Manager IP address is correctly configured in the agent setup.  
- Check network connectivity between endpoints and the Wazuh server.  
- Review agent logs for errors (`/var/ossec/logs/ossec.log` on Linux or `C:\Program Files (x86)\ossec-agent\ossec.log` on Windows).  

---

## **References**
- [Wazuh Documentation](https://documentation.wazuh.com/)  
- [Wazuh GitHub Repository](https://github.com/wazuh/wazuh)  
- [Wazuh Community Forum](https://wazuh.com/community/)  

---

## **Contributing**

Contributions are welcome! If you have suggestions or find issues, please submit a pull request or open an issue.

---

## **License**
This repository is licensed under the [MIT License](LICENSE).

# Wazuh-Installation-Guide-Pre-Built-Virtual-Machine-OVA-
This repository provides a comprehensive, step-by-step guide to installing and configuring Wazuh using the pre-built Virtual Machine (OVA) format. Whether you're setting up Wazuh for monitoring and security analytics or exploring its powerful dashboard features, this guide simplifies the process.


Here’s a step-by-step guide to install Wazuh using the Virtual Machine (OVA) for your GitHub repository:

---

## Step-by-Step Guide: Installing Wazuh Using the Virtual Machine (OVA)

### 1. **Download the Wazuh Virtual Appliance (OVA)**
   - Download the pre-built Wazuh OVA file for version 4.9.2 from [Wazuh's official site](https://packages.wazuh.com/4.x/vm/wazuh-4.9.2.ova).
   - The OVA includes the following components:
     - **Amazon Linux 2**
     - **Wazuh manager 4.9.2**
     - **Wazuh indexer 4.9.2**
     - **Filebeat-OSS 7.10.2**
     - **Wazuh dashboard 4.9.2**

### 2. **Check System Requirements**
   - Ensure your host system is 64-bit.
   - Enable **hardware virtualization** in the firmware (BIOS/UEFI) of your host.
   - Install a virtualization platform like **VirtualBox** or **VMware** or **Hyper-V**.

   **Default Hardware Configuration for Wazuh VM:**
   - **CPU:** 4 cores
   - **RAM:** 8 GB
   - **Storage:** 50 GB

   *Note:* Modify the configuration based on your needs.

### 3. **Import the OVA File**
   - Open your virtualization platform (e.g., VMware).
   - Import the downloaded OVA file:
     - In VMware, go to `File > Open...`

![image](https://github.com/user-attachments/assets/46a49ab8-5e5a-4472-a4b0-6cbff558eb4b)

   - Select the Wazuh OVA file and click on `Open`
     
![image](https://github.com/user-attachments/assets/7ec0e9ac-a47e-452a-ba0a-41e9fa36e673)

   - In the new open windows, give a name to your VM (e,g : Wuzuh Server), choose the path where to store your VM configuraton files and then click on **Import**.

![image](https://github.com/user-attachments/assets/230a2067-85c4-483d-b890-6d58bb2c4860)

  - Your VM has been successfully imported. You can now add more RAM (e,g: from 8Gb to 10Gb), Storage ( From 50 Gb to 80Gb) and CPUs (4 to 8) if you want or have more resources. Also choose the correct network  adapter (e.g, from bridge to NAT) for the sake of this demo.

![image](https://github.com/user-attachments/assets/9aa9af73-ffdd-4e5b-aee3-817e1148fa42)

### 4. **Start the Virtual Machine**
   - Start the VM from your virtualization platform by clicking on `Power on this virtual machne`.
   - Login credentials for the VM:
     - **Username:** `wazuh-user`
     - **Password:** `wazuh`

![image](https://github.com/user-attachments/assets/41f07473-a830-4399-aeaa-4035182de09c)


### 6. **Find the VM's IP Address**
   - Inside the VM, run the following command to get the IP address:
     ```bash
     ip a
     ```
![image](https://github.com/user-attachments/assets/6a4d5a8b-95d6-4b2e-843e-5132f8dba0db)


### 7. **Access the Wazuh Dashboard**
   - Open a web browser from another oon the same network (e.g, Debian or Windows) and navigate to:
     ```text
     https://<wazuh_server_ip>
     ```
   - Replace `<wazuh_server_ip>` with the IP address obtained in the previous step.
   - If pop-pup windows open, click on `Advaanced` and then click on `Accept the Risk and Continue`

![image](https://github.com/user-attachments/assets/bd43b0cc-1a3b-45cf-8a8a-c00e8eacfc2d)

   - Dashboard login credentials:
     - **Username:** `admin`
     - **Password:** `admin`

![image](https://github.com/user-attachments/assets/68665414-a4b5-4895-8201-194886af8bc7)

 - You have successfully install the wauh server using the OVA file.

![image](https://github.com/user-attachments/assets/f56e49b0-54a7-47d8-aac2-a78a48eba84f)

---

### Additional Notes
- Adjust hardware settings in the virtualization platform if needed to handle more endpoints or data.
- SSH login as `root` is disabled by default. Use the `wazuh-user` account with `sudo` privileges for administrative tasks.
- Change the default password with a strong password
---

Feel free to copy this guide into your GitHub repository. Let me know if you need help formatting or customizing it further!

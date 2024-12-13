# Wazuh-Installation-Guide-Pre-Built-Virtual-Machine-OVA-
This repository provides a comprehensive, step-by-step guide to installing and configuring Wazuh using the pre-built Virtual Machine (OVA) format. Whether you're setting up Wazuh for monitoring and security analytics or exploring its powerful dashboard features, this guide simplifies the process.


Here’s a step-by-step guide to install Wazuh using the Virtual Machine (OVA) for your GitHub repository:

---

## Step-by-Step Guide: Installing Wazuh Using the Virtual Machine (OVA)

### 1. **Download the Wazuh Virtual Appliance (OVA)**
   - Download the pre-built Wazuh OVA file for version 4.9.2[https://wazuh.com/download/](https://packages.wazuh.com/4.x/vm/wazuh-4.9.2.ova).
   - The OVA includes the following components:
     - **Amazon Linux 2**
     - **Wazuh manager 4.9.2**
     - **Wazuh indexer 4.9.2**
     - **Filebeat-OSS 7.10.2**
     - **Wazuh dashboard 4.9.2**

### 2. **Check System Requirements**
   - Ensure your host system is 64-bit.
   - Enable **hardware virtualization** in the firmware (BIOS/UEFI) of your host.
   - Install a virtualization platform like **VirtualBox**.

   **Default Hardware Configuration for Wazuh VM:**
   - **CPU:** 4 cores
   - **RAM:** 8 GB
   - **Storage:** 50 GB

   *Note:* Modify the configuration based on your needs.

### 3. **Import the OVA File**
   - Open your virtualization platform (e.g., VirtualBox).
   - Import the downloaded OVA file:
     - In VirtualBox, go to `File > Import Appliance`.
     - Select the Wazuh OVA file and follow the prompts.

### 4. **Configure Display Settings**
   - In VirtualBox, adjust the graphic controller to prevent freezing issues:
     - Select the imported VM.
     - Click `Settings > Display`.
     - Set the **Graphic Controller** to `VMSVGA`.

### 5. **Start the Virtual Machine**
   - Start the VM from your virtualization platform.
   - Login credentials for the VM:
     - **Username:** `wazuh-user`
     - **Password:** `wazuh`
   - To escalate to root privileges, run:
     ```bash
     sudo -i
     ```

### 6. **Find the VM's IP Address**
   - Inside the VM, run the following command to get the IP address:
     ```bash
     ip a
     ```

### 7. **Access the Wazuh Dashboard**
   - Open a web browser and navigate to:
     ```text
     https://<wazuh_server_ip>
     ```
   - Replace `<wazuh_server_ip>` with the IP address obtained in the previous step.
   - Dashboard login credentials:
     - **Username:** `admin`
     - **Password:** `admin`

---

### Additional Notes
- Adjust hardware settings in the virtualization platform if needed to handle more endpoints or data.
- SSH login as `root` is disabled by default. Use the `wazuh-user` account with `sudo` privileges for administrative tasks.

---

Feel free to copy this guide into your GitHub repository. Let me know if you need help formatting or customizing it further!

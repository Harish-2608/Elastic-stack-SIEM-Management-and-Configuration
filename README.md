# Elastic Stack SIEM Management and Configuration 

This project will take you on an adventurous journey of setting up a powerful Security Information and Event Management (SIEM) solution. Let's dive into the action and uncover the secrets of securing systems like a pro!

---

## Quick Overview

| **Step**                          | **Description**                                                                                 |
|-----------------------------------|-----------------------------------------------------------------------------------------------|
| **1. Set Up Linux VM**            | Install and configure a Linux-based virtual machine.                                           |
| **2. Elastic Cloud Setup**        | Create an account and log in to Elastic Cloud.                                                 |
| **3. Configure Elastic Defend**   | Install the Elastic Agent to collect logs and gain visibility.                                 |
| **4. Collect Logs Using Nmap**    | Run Nmap scans and forward logs to Elastic Stack.                                              |
| **5. Visualize Events**           | Create dashboards for better insights.                                                        |
| **6. Configure Security Alerts**  | Set up alerts to detect and monitor Nmap activities.                                           |

---

## Detailed Steps

### 1. Set Up a Linux Virtual Machine
The Linux VM will serve as the target machine for log collection.

1. Install and configure a Linux-based VM using VMware or VirtualBox.
2. Update and secure your Linux VM as necessary.

### 2. Elastic Cloud Setup
1. Create an account in Elastic Cloud.
2. Log in to your Elastic Cloud account.

### 3. Configure Elastic Defend Integration
Elastic Defend provides detection, prevention, and response capabilities with deep visibility for SIEM and EDR use cases across Windows, Linux, and macOS platforms.

#### Steps:
1. Navigate to **Integrations** in Elastic Cloud.
2. Search for and select **Elastic Defend**.
3. Follow the installation steps:
   - Copy the provided configuration code.
   - Paste the code into your Linux VM terminal.

4. Wait a few minutes for the Elastic Agent to install. Once installed, you should see:
   
5. Verify the installation using the following command:
   ``` bash
   sudo systemctl status elastic-agent.service
   ```

### 4. Collect Logs Using Nmap
1. Run Nmap on the Linux VM to generate logs:
   ```bash
   nmap -Pn -A <ip>
   ```
   Nmap, a network scanning tool, generates logs for port scans and services, simulating security incidents.

2. Go to **Observability** > **Logs** in Elastic Cloud.
3. Search for:
   ```
   process.args: "nmap"
   ```
4. Observe the generated events.

### 5. Visualize Events
1. Navigate to **Analytics** > **Dashboards**.
2. Click **Create Dashboard**.
3. Add visualizations based on the logs collected.

### 6. Configure Security Alerts
Since our focus is on security, we will configure alerts for detecting Nmap scan activities.

1. Go to **Security** > **Alerts**.
2. Click **Manage Rules** and select **Create New Rule**.
3. Configure a **Custom Query** rule:
   - **Custom Query:**
     ```
     event.action: "nmap_scan"
     ```
   - **Rule Name:**
     `Detect Nmap Scan`
   - **Description:**
     `Detects events related to Nmap scanning activities.`
   - **Severity Level:**
     Set based on importance (e.g., Medium, High).
   - Leave default settings under **Schedule Rule**.

4. Click **Continue** and then **Create and Enable Rule**.

### 7. Monitor Alerts
1. Go to the **Alerts** section under **Security**.
2. If an Nmap scan event is detected, it will appear in the alerts dashboard.

---

## Key Features
- **Elastic Defend Integration:** Provides SIEM and EDR capabilities.
- **Nmap Log Collection:** Demonstrates log collection and event creation for security incidents.
- **Custom Alerts:** Enables monitoring of specific activities like Nmap scans.

---

##  Conclusion
This project demonstrates how to set up Elastic Stack for SIEM, configure Elastic Defend, and create security alerts to monitor and visualize events.

---

Keep hacking, learning, and protecting! 

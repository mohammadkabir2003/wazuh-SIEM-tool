# 🛡️ Wazuh Home Lab Deployment

## 📌 Project Overview
This project is a **Wazuh-based Security Information and Event Management (SIEM) setup** deployed in my home lab environment.  
The goal was to monitor, analyze, and respond to security events across my network by running **Wazuh Manager** inside a Docker container and installing **Wazuh Agents** on various systems — including the main server itself — to collect and forward security logs.

---

## 🛠 Tools & Technologies Used
- **[Wazuh](https://wazuh.com/)** – Open-source SIEM and XDR platform for threat detection, monitoring, and incident response.
- **Docker & Docker Compose** – Containerized deployment of the Wazuh Manager, Indexer, and Dashboard.
- **Ubuntu Server** – Main OS hosting the Wazuh Docker environment.
- **Dynamic DNS (DDNS)** – Allows remote access to the Wazuh Dashboard and manager from external networks.
- **UFW Firewall** – Securing and allowing specific ports for agent-manager communication.
- **SSH** – Secure remote access to the server for configuration and management.

---

## ⚙️ Features Implemented
- **Wazuh Manager Deployment** via Docker Compose (single-node setup).
- **Wazuh Dashboard** for visual monitoring and security analysis.
- **Wazuh Agent** installed on Ubuntu to forward logs to the manager.
- **Firewall Configuration** to enable secure communication on ports 1514, 1515, and 55000.

---

## 🚧 Challenges Faced
1. **Conflicts Between Manager & Agent on the Same Machine**  
   - Initially tried running both on the same system, but package conflicts (`wazuh-agent` vs `wazuh-manager`) caused installation errors.
   
2. **Configuration Errors in `ossec.conf`**  
   - Encountered “Invalid element” errors (`vulnerability-detection`, `indexer`) due to misconfigured XML tags.  
   - Fixed by locating and removing/adjusting problematic tags in `ossec.conf`.

3. **Agent Not Appearing on Dashboard**  
   - Caused by incorrect manager IP in agent configuration and blocked firewall ports.  
   - Resolved by updating `/var/ossec/etc/ossec.conf` with the correct IP/DDNS and allowing ports in UFW.

4. **Permission Issues Editing Config Files in Docker**  
   - Needed to edit `wazuh.yml` and `ossec.conf` inside the container with elevated permissions.

---

## 🔮 Future Improvements / Next Steps
- **Multi-Agent Deployment**  
  Install agents on multiple VMs, desktops, and IoT devices for wider coverage.
  
- **Windows Agent Integration**  
  Deploy Wazuh agents on Windows systems to monitor system logs and events.
  
- **Log Enrichment**  
  Integrate threat intelligence feeds to enhance detection capabilities.

- **Alert Automation**  
  Set up active responses (e.g., auto-block IPs via firewall when threats detected).

- **Cloud Integration**  
  Monitor cloud-based services (AWS, Azure, GCP) by connecting them to Wazuh.

- **Centralized Logging with ELK**  
  Expand Wazuh’s indexer to integrate with Elasticsearch and Kibana for advanced analytics.

---

## 📷 Screenshots
There are screenshots that show the journey. Please take a look at the docs file. 

---

## 📚 References
- [Installing Wazuh SIEM Server on Ubuntu using Docker](https://www.youtube.com/watch?v=aaQc_3eF5PU&t=1s&ab_channel=MBTECH)
- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Docker Compose for Wazuh](https://github.com/wazuh/wazuh-docker)
- [Wazuh Agent Installation Guide](https://documentation.wazuh.com/current/installation-guide/wazuh-agent/index.html)

---

## 💡 Author
**Your Name** – [Your GitHub Profile](https://github.com/yourusername)

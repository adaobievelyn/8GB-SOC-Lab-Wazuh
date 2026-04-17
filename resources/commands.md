# Commands Reference — 8GB SOC Lab (Wazuh SIEM)

This file contains all commands used throughout the project, organized by phase.

# 1. Ubuntu Server (Wazuh Manager)

## Update System
```bash
sudo apt update && sudo apt upgrade -y
```

## Check IP Address
```bash
ip a
```

## Install Wazuh (All-in-One)
```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash wazuh-install.sh -a
```

## Retrieve Wazuh Credentials (if login fails)
```bash
sudo /var/ossec/bin/wazuh-passwords-tool.sh
```

## Check Wazuh Services
```bash
sudo systemctl status wazuh-manager
sudo systemctl status wazuh-indexer
sudo systemctl status wazuh-dashboard
```

## Restart Wazuh Services
```bash
sudo systemctl restart wazuh-manager
sudo systemctl restart wazuh-indexer
sudo systemctl restart wazuh-dashboard
```

# 2. SSH Access (Headless Management)

## Connect to Server
```bash
ssh username@<SERVER-IP>
```

## Fix SSH Host Key Error
```bash
ssh-keygen -R <SERVER-IP>
```

# 3. Windows 11 Setup & Optimization

## OOBE Bypass (Skip Internet Requirement)
```cmd
OOBE\BYPASSNRO
```

## Start Wazuh Agent Service
```cmd
NET START Wazuh
```

## Stop Wazuh Agent
```cmd
NET STOP Wazuh
```

# 4. Windows Wazuh Agent Installation

## Download Agent (PowerShell)
```powershell
Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.7.5-1.msi -OutFile $env:temp\wazuh-agent.msi
```

## Install Agent
```powershell
msiexec.exe /i $env:temp\wazuh-agent.msi /q WAZUH_MANAGER='<SERVER-IP>' WAZUH_REGISTRATION_SERVER='<SERVER-IP>' WAZUH_AGENT_NAME='Windows-Endpoint'
```

---

# 5. Linux Endpoint (Lubuntu)

## Update System
```bash
sudo apt update && sudo apt upgrade -y
```

## Install Wazuh Agent (Debian-based)
```bash
curl -sO https://packages.wazuh.com/4.x/wazuh-agent_4.7.5-1_amd64.deb
sudo dpkg -i wazuh-agent_4.7.5-1_amd64.deb
```

## Configure Manager (Edit Config)
```bash
sudo nano /var/ossec/etc/ossec.conf
```

(Change the manager IP inside the file)

## Enable & Start Agent
```bash
sudo systemctl daemon-reexec
sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

## Check Agent Status
```bash
sudo systemctl status wazuh-agent
```

# 6. Agent Verification

## List Agents (Manager Side)
```bash
sudo /var/ossec/bin/agent_control -l
```

# 7. VirtualBox (Key Operations)

## Start VM in Headless Mode (CLI)
```bash
VBoxManage startvm "Wazuh-Manager" --type headless
```

## List VMs
```bash
VBoxManage list vms
```

# 8. Troubleshooting Commands

## Check System Memory
```bash
free -h
```

## Check Running Processes
```bash
top
```

## Kill Process
```bash
kill -9 <PID>
```

## Check Open Ports
```bash
sudo ss -tulnp
```

## Restart Networking
```bash
sudo systemctl restart networking
```

# 9. Useful File Paths

| Purpose        | Path                      |
|----------------|---------------------------|
| Wazuh Config   | /var/ossec/etc/ossec.conf |
| Wazuh Logs     | /var/ossec/logs/          |
| Agent Binary   | /var/ossec/bin/           |


# 10. Validation Checklist Commands

Run these to confirm everything is working:

## Manager
```bash
sudo systemctl status wazuh-manager
```

## Agent (Linux)
```bash
sudo systemctl status wazuh-agent
```

## Agent (Windows)
```cmd
NET START Wazuh
```


# Notes

- Replace `<SERVER-IP>` with your actual Wazuh Manager IP
- Always verify services after installation
- If something fails, check logs before retrying

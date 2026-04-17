# 4. Agent Enrollment

## Windows Agent

Open PowerShell (Admin)

Run:

Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.7.5-1.msi -OutFile $env:temp\wazuh-agent.msi

Install:

msiexec.exe /i $env:temp\wazuh-agent.msi /q WAZUH_MANAGER='YOUR-IP' WAZUH_AGENT_NAME='Windows'

Start service:

NET START Wazuh

---

## Linux Agent

Run:

sudo apt install wazuh-agent

Edit config:
sudo nano /var/ossec/etc/ossec.conf

Set the manager IP


## Start agent

sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent

## Expected Result

Both agents appear in the Wazuh dashboard

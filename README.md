# The 8GB SOC Lab: Building a Multi-Endpoint Wazuh SIEM Under Extreme Constraints

## Project Overview
This project demonstrates how to build a fully functional Security Operations Center (SOC) lab using Wazuh SIEM on a system with only 8GB RAM.

The lab includes:
- 1 Wazuh Manager (Ubuntu Server)
- 1 Windows 11 Endpoint
- 1 Linux Endpoint (Lubuntu)

All systems are monitored in real-time through the Wazuh dashboard.


## Objective
To prove that practical SOC and SIEM skills can be developed under hardware constraints by applying system optimization and troubleshooting techniques.


## Lab Architecture

| Component | OS | Purpose |
|----------|----|--------|
| Wazuh Manager | Ubuntu Server 22.04 | Log collection & analysis |
| Endpoint 1 | Windows 11 | Attack simulation / monitoring |
| Endpoint 2 | Lubuntu | Lightweight monitored system |

graph TD
    subgraph Host_Machine_8GB_RAM
        subgraph VirtualBox_Network_Bridge
            Manager[Wazuh Manager <br/> Ubuntu Server]
            Win11[Windows 11 Agent <br/> Victim Machine]
            Lubuntu[Lubuntu Agent <br/> Linux Node]
        end
    end

    Win11 -- Port 1514/1515 --> Manager
    Lubuntu -- Port 1514/1515 --> Manager
    Manager -- Dashboard Interface --> Host_Browser[Host Web Browser]
    
Network Mode: Bridged Adapter (All machines on the same network)


## Hardware Constraint

- Host RAM: 8GB
- Virtualization Tool: VirtualBox


## Key Concept

This project focuses on:
- Running enterprise tools on limited hardware
- Memory optimization
- Real-world troubleshooting


## Project Structure

- `/setup-guides` → Step-by-step installation guides
- `/resources` → Commands and reference materials
- `/screenshots` → Proof of working lab


## Start Here

Follow the guides in this exact order:

1. Wazuh Manager Setup  
2. Windows Endpoint Setup  
3. Lubuntu Endpoint Setup  
4. Agent Enrollment  
5. Troubleshooting  


## Final Result

<img width="1919" height="868" alt="Screenshot 2026-04-16 130300" src="https://github.com/user-attachments/assets/8148b8a8-88a8-48e0-ab93-78d193bb65fa" />


## Skills Demonstrated

- SIEM Deployment (Wazuh)
- Linux Administration
- Windows System Optimization
- Virtualization (VirtualBox)
- Network Configuration
- Troubleshooting under constraints


## Important Note

This guide is written for beginners. Every step is explained.

If something fails, check the troubleshooting section before restarting.

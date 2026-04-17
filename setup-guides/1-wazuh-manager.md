# 1. Wazuh Manager Setup (Ubuntu Server)

## Step 1: Download Ubuntu Server

Download:
https://ubuntu.com/download/server

File name:
ubuntu-22.04.4-live-server-amd64.iso


## Step 2: Create Virtual Machine

Open VirtualBox → Click "New"

Name: Wazuh-Manager  
Type: Linux  
Version: Ubuntu (64-bit)

## Step 3: Allocate Resources

RAM: 2048 MB  
CPU: 2 cores  
Storage: 20GB (Dynamic)

## Step 4: Configure Network

Settings → Network  
Adapter 1 → Bridged Adapter  

Why:
This allows the VM to behave like a real machine on your network.

## Step 5: Install Ubuntu Server

Start VM → Select ISO → Install Ubuntu Server

IMPORTANT:
- Choose minimal install
- Do NOT install GUI


## Step 6: Get IP Address

After installation:

Run:
ip a

Look for:
192.168.x.x

Save this IP — you will use it later.


## Step 7: Install Wazuh

Run:

curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash wazuh-install.sh -a


## Step 8: Access Dashboard

Open browser on host:

https://<YOUR-IP>

## Step 9: Login

If the password fails:

Run:
sudo /var/ossec/bin/wazuh-passwords-tool.sh


## Expected Result

You should see the Wazuh dashboard.

If not → go to the troubleshooting section.

# 01 - Creating Virtual Machines in Azure

# Objectives
This section demonstrates how to create Azure Virtual Machines using three different methods:

- **Azure Portal**
- **Azure CLI**
- **Azure PowerShell**
ac
---

## ✅ Prerequisites

- An active Azure subscription
- Access to Azure Portal, or Azure CLI/PowerShell installed and authenticated

---

## 🖥️ Create a VM via Azure Portal

1. Sign in to [Azure Portal](https://portal.azure.com)
2. Search for **Virtual Machines** in the top search bar
3. Click **+ Create > Azure virtual machine**
4. Fill out the **Basics** tab:
   - **Subscription** and **Resource Group**
   - **VM name** (e.g., `myPortalVM`)
   - **Region**: East US
   - **Image**: Ubuntu LTS or Windows
   - **Authentication type**: Password or SSH public key
   - **Username** and **Password**
5. Configure **Disks**, **Networking**, and **Management** as needed
6. Click **Review + create**, then **Create**

📸 Example:

![Azure Portal - Create VM](images/vm-portal-create.png)

---

## 💻 Create a VM using Azure CLI

```bash
# Create a resource group
az group create --name vm-rg --location eastus

# Create an Ubuntu VM
az vm create \
  --resource-group vm-rg \
  --name myCLIVM \
  --image UbuntuLTS \
  --admin-username azureuser \
  --authentication-type ssh \
  --generate-ssh-keys

# Open port 22 for SSH
az vm open-port --resource-group vm-rg --name myCLIVM --port 22

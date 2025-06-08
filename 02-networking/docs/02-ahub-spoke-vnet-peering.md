# 01 - Create Hub-and-Spoke VNets with Subnets and Peering

## 🧭 Scenario

You're tasked with building the foundation for a secure hub-and-spoke Azure network architecture for a web-based application. This involves creating two VNets, configuring subnets, and setting up VNet peering to enable secure communication.

---

## 🎯 Requirements

- **hub-vnet**:
  - Address space: `10.0.0.0/16`
  - Subnet: `firewall-subnet` - `10.0.1.0/24`

- **app-vnet**:
  - Address space: `10.1.0.0/16`
  - Subnets:
    - `frontend` - `10.1.1.0/24`
    - `backend` - `10.1.2.0/24`

- **Peering**:
  - Allow VNet-to-VNet traffic (both directions)
  - Both VNets in the **same region**

---

## 🛠️ Azure Portal Steps

### Step 1: Create VNets

1. Go to **Azure Portal > Virtual Networks**.
2. Click **Create** and choose:
   - Name: `hub-vnet`
   - Address space: `10.0.0.0/16`
   - Subnet name: `firewall-subnet`
   - Subnet range: `10.0.1.0/24`
   - Region: `East US`
   - Click **Review + Create**

3. Repeat for `app-vnet`:
   - Address space: `10.1.0.0/16`
   - Subnet: `frontend`, range: `10.1.1.0/24`
   - After creation, go to **Subnets > Add**:
     - Name: `backend`
     - Range: `10.1.2.0/24`

---

### Step 2: Configure VNet Peering

1. Go to `hub-vnet` > **Peerings** > **Add**:
   - Peering name: `HubToApp`
   - Remote VNet: `app-vnet`
   - Allow traffic: ✅ Allow virtual network access

2. Go to `app-vnet` > **Peerings** > **Add**:
   - Peering name: `AppToHub`
   - Remote VNet: `hub-vnet`
   - Allow traffic: ✅ Allow virtual network access

---

## ⚡ Azure CLI Steps



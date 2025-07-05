# 05 - Create and Configure Azure Firewall

## 🧠 Objective

Deploy Azure Firewall in a hub-spoke architecture and configure rules to manage and inspect traffic.

---

## 🗂️ Prerequisites

- A **Hub Virtual Network** (`hub-vnet`)
- A **Subnet** named `AzureFirewallSubnet` (this name is required) in the hub VNet
- Optional: A spoke VNet with VNet peering to the hub VNet
- A Public IP (Standard SKU)

---

## 🔧 Step 1: Create AzureFirewallSubnet

> Required for firewall deployment

1. Go to **Virtual networks** > Select `hub-vnet`
2. Under **Subnets**, click **+ Subnet**
3. Set:
   - **Name**: `AzureFirewallSubnet`
   - **Address range**: e.g., `10.0.1.0/26`
4. Leave the rest default and click **Add**

---

## 🌐 Step 2: Create Public IP for Firewall

1. Go to **Create a resource** > **Networking** > **Public IP address**
2. Name: `firewall-pip`
3. SKU: **Standard**
4. IP version: IPv4
5. Assignment: Static
6. Click **Review + Create**, then **Create**

---

## 🔥 Step 3: Deploy Azure Firewall

1. Go to **Create a resource** > **Networking** > **Firewall**
2. Fill in:
   - **Name**: `azure-fw`
   - **Region**: same as your hub VNet
   - **Firewall management**: Azure Firewall
   - **Tier**: Choose **Standard** or **Premium**
3. **Virtual network**: Select `hub-vnet`
4. **Public IP**: Select `firewall-pip`
5. Click **Review + Create**, then **Create**

---

## 🛡️ Step 4: Create Firewall Rules

> You can create **Network rules**, **Application rules**, or **NAT rules**.

### Option A: Create Application Rule

1. Go to **Firewall Manager** > `azure-fw` > **Rules**
2. Click **+ Add rule collection**
3. Type: `Application`
4. Name: `AppRuleCollection1`
5. Priority: `100`
6. Action: Allow
7. Rules:
   - Name: `AllowWeb`
   - Source addresses: `*`
   - Protocol: `HTTP`, `HTTPS`
   - Target FQDNs: `www.microsoft.com`
8. Click **Add**

### Option B: Create Network Rule

1. Follow similar steps but choose `Network` rule collection
2. Define:
   - Source IP ranges
   - Destination IP/ports
   - Protocol: TCP/UDP

---

## 🔁 Optional: Route Traffic via Firewall (User-Defined Routes)

> Send traffic through Azure Firewall from a spoke VNet

1. Create a route table:
   - Name: `fw-route-table`
2. Add a route:
   - Name: `DefaultRoute`
   - Address prefix: `0.0.0.0/0`
   - Next hop: **Virtual appliance**
   - IP: Firewall’s private IP
3. Associate this route table with the spoke subnet

---

## 🔍 Verify Firewall Functionality

- From a VM in the spoke network, try accessing external sites
- Traffic should now pass through Azure Firewall based on your rule set

---

## 📌 Notes

- Azure Firewall requires **Standard Public IP**
- The subnet name must be **AzureFirewallSubnet**
- UDR is needed to force traffic from spoke → hub
- Application rules work with FQDNs (DNS required)

---

## 📸 Screenshots

> [Place screenshots under `compute/docs/images` and reference them here if documenting]

---

## ✅ Outcome

You've successfully deployed and configured Azure Firewall in a hub-spoke network to manage and inspect egress traffic.


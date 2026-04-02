# networking-topology-lab
The documentation of the continuously evolving data network 

##Cisco Catalyst 9105AXI AP

# Cisco EWC AP Deployment Workflow

## 🔄 Step-by-Step Setup Order

### 1. Define WLANs (SSIDs)
- Go to: `Configuration → Tags & Profiles → WLANs`
- Create each SSID:
  - `MainNet` (VLAN 10)
  - `IoTNet` (VLAN 20)
  - `GuestNet` (VLAN 30)
- Set:
  - SSID name
  - WLAN ID
  - Security (WPA2 Personal, etc.)

---

### 2. Define Policy Profiles
- Go to: `Configuration → Tags & Profiles → Policy`
- For each VLAN:
  - Create a Policy Profile (e.g., `MainNet_Policy`)
  - Set the correct VLAN ID (e.g., 10, 20, 30)
  - Leave other options default unless needed

---

### 3. Assign Policy Profiles to WLANs
- Edit each WLAN
- Under "Policy Profile", attach the correct one:
  - `MainNet` → `MainNet_Policy`
  - `IoTNet` → `IoT_Policy`
  - `GuestNet` → `Guest_Policy`

---

### 4. (Optional) Define WLAN Tag
- Most setups use the **default WLAN tag**
- Only needed if doing multi-site/AP-grouping setups

---

### 5. Apply WLANs + Policies to the AP
- Go to: `Configuration → Access Points → [Your AP]`
- Under **Tags**:
  - Assign WLANs (SSIDs)
  - Assign Policy Profile (per SSID)

---

### 6. Save the Configuration
- In CLI:
  ```cisco
  write memory

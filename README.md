# 📦 Intune Detected Apps Report

This PowerShell script generates a full report of all detected applications across managed devices in Microsoft Intune using the Microsoft Graph API (beta). It includes details such as the app name, version, publisher, platform, and user assigned to each device.

---

## 🚀 Features

- Retrieves all managed devices using `/deviceManagement/managedDevices`
- Queries each device's detected apps using `/deviceManagement/managedDevices/{id}/detectedApps`
- Includes the user display name linked to each device
- Uses Microsoft Graph batching for optimal performance
- Outputs a clean `.csv` file report

---

## 📥 Output Example

| UserDisplayName | DeviceName | AppDisplayName | Version | Publisher | Platform | AppId |
|------------------|------------|----------------|---------|-----------|----------|--------|
| john doe         | LAPTOP-001 | Microsoft Edge | 125.0   | Microsoft | Windows  | abc123 |
| jane smith       | PC-448     | Zoom           | 5.17.1  | Zoom Inc. | Windows  | def456 |

---

## 🧰 Requirements

- PowerShell 7+ (recommended)
- Microsoft.Graph module  
- Permissions: `DeviceManagementManagedDevices.Read.All`

---

## 🛠️ Installation

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser
Connect-MgGraph -Scopes "DeviceManagementManagedDevices.Read.All"
```

---

## ▶️ Usage

```plain
.\Intune-EntraDetectedAppsReport.ps1
```

The report will be saved in the same folder with the format:

DetectedApps_Report_YYYYMMDD_HHmm.csv

---

## ⏱ Performance

Supports up to 1000+ devices using batched queries of 20 devices per round. Execution time will vary depending on number of devices and apps.


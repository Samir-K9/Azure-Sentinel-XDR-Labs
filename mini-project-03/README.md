# Mini Project 03 — Endpoint Security with Microsoft Defender for Endpoint & Intune

**Tools Used:** Microsoft Defender XDR · Microsoft Intune · VMware Workstation Pro · Atomic Red Team
**Focus:** Endpoint onboarding, device management, Attack Surface Reduction policy configuration, and threat simulation

---

## Overview

This project covers endpoint security using Microsoft Defender for Endpoint and Microsoft Intune. The goal was to onboard a Windows 11 virtual machine to Defender for Endpoint and Intune, configure Attack Surface Reduction policies to harden the endpoint, and simulate real-world attack techniques using Atomic Red Team to validate detections in Microsoft Defender.

---

## Table of Contents

1. [Create a Windows 11 VM in VMware Workstation Pro](#1-create-a-windows-11-vm-in-vmware-workstation-pro)
2. [Configure Advanced Features in Microsoft Defender](#2-configure-advanced-features-in-microsoft-defender)
3. [Onboard the VM to Microsoft Defender for Endpoint](#3-onboard-the-vm-to-microsoft-defender-for-endpoint)
4. [Run the Onboarding Package](#4-run-the-onboarding-package)
5. [Configure Automatic Enrollment in Intune](#5-configure-automatic-enrollment-in-intune)
6. [Enable Microsoft Defender for Endpoint Integration in Intune](#6-enable-microsoft-defender-for-endpoint-integration-in-intune)
7. [Create an Attack Surface Reduction Policy](#7-create-an-attack-surface-reduction-policy)
8. [Install Atomic Red Team on the VM](#8-install-atomic-red-team-on-the-vm)
9. [Invoke T1547.001 and Observe Alert in Defender](#9-invoke-t1547001-and-observe-alert-in-defender)

 ---

## Steps

### 1. Create a Windows 11 VM in VMware Workstation Pro

Created a Windows 11 virtual machine using VMware Workstation Pro to act as the test endpoint for this lab. This VM will be onboarded to Microsoft Defender for Endpoint and managed through Microsoft Intune, simulating a real-world enterprise endpoint environment.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/a782402c1c07a7c8bbbc98f027a35c8647ceaa23/mini-project-03/screenshots/Screenshot%202026-03-26%20111043.png)

---

### 2. Configure Advanced Features in Microsoft Defender

Navigated to Settings → Endpoints → Advanced Features in the Microsoft Defender XDR portal and enabled the following settings before onboarding the endpoint:

- EDR in Block Mode: allows Defender for Endpoint to block malicious artifacts even when a third-party antivirus is the primary solution.
- Custom Network Indicators: enables the use of custom IP, URL, and domain indicators for threat detection and blocking.
- Web Content Filtering: allows monitoring and blocking of websites based on content categories.
- Microsoft Intune Connection: links Defender for Endpoint with Intune to enable unified endpoint security and compliance management.

---

### 3. Onboard the VM to Microsoft Defender for Endpoint

Signed into the Windows 11 VM using Bob Smith's user account. Navigated to Settings → Endpoints → Device Management → Onboarding in the Microsoft Defender XDR portal and downloaded the onboarding package. This package is used to register the VM as a managed endpoint in Microsoft Defender for Endpoint.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/9f23f2c957206ac8ba0eabf339fed92f65f75bfb/mini-project-03/screenshots/Screenshot%202026-03-26%20112616.png)

---

### 4.Run the Onboarding Package

Extracted the onboarding package downloaded in the previous step and ran it as administrator on the Windows 11 VM. This executes the onboarding script that registers the device with Microsoft Defender for Endpoint and begins sending security telemetry to the Defender portal

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/f6a38c13eb9e757bfa3fa746f23c495d174938d0/mini-project-03/screenshots/Windows%2011%20x64-2026-03-26-11-33-38.png)

Once successfully onboarded, the device appeared under Assets → Devices in the Microsoft Defender XDR portal, confirming the endpoint was registered and communicating with Defender.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/044031380c449abc532796bec582359a5998765c/mini-project-03/screenshots/Screenshot%202026-03-26%20113618.png)

---

### 5. Configure Automatic Enrollment in Microsoft Intune

Navigated to Intune → Devices → Onboarding → Enrollment → Automatic Enrollment and set the MDM User Scope to All. This enables all users in the tenant to have their devices automatically enrolled into Intune mobile device management when they sign in, allowing Intune to manage and apply policies to the onboarded VM.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/40296d6b1b26f7485da40294dcfc587da45e513f/mini-project-03/screenshots/Screenshot%202026-03-26%20114600.png)

Since the VM was already signed in using Bob Smith's account, the device appeared automatically in Intune under Devices, confirming successful enrollment.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/a57c619134c2cedb77170adfe6fdc29dd102868e/mini-project-03/screenshots/Screenshot%202026-03-26%20114827.png)

---

### 6. Enable Microsoft Defender for Endpoint Integration in Intune

Navigated to Endpoint Security → Microsoft Defender for Endpoint in Intune and enabled the following two settings:

- Allow Microsoft Defender for Endpoint to enforce Endpoint Security Configurations: allows Defender for Endpoint to push and enforce security configurations directly on managed devices
- Connect Windows devices version 10.0.15063 and above to Microsoft Defender for Endpoint: enables Windows 10 and Windows 11 devices enrolled in Intune to be connected to and monitored by Defender for Endpoint

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/df0181ac5a90b5a65455d84b131e14b5aedb9bdf/mini-project-03/screenshots/Screenshot%202026-03-26%20115526.png)

---

### 7. Create an Attack Surface Reduction Policy

Created an Attack Surface Reduction (ASR) policy in Intune to reduce the attack surface of the onboarded endpoint by blocking common attack techniques. As this is a test environment, only a few rules were enabled. The policy was applied to all devices in the tenant. Rules applied:

- Block all Office applications from creating child processes: prevents Office applications like Word and Excel from spawning child processes, a common technique used by malware delivered through malicious documents.
- Block credential stealing from the Windows local security authority subsystem: protects the LSASS process from being dumped by attackers attempting to harvest credentials from memory.
- Use advanced protection against ransomware: enables heuristic-based protection to detect and block ransomware behaviour before it can encrypt files.
- Block process creations originating from PSExec and WMI commands: prevents attackers from using PSExec and WMI as lateral movement or remote execution techniques, commonly seen in living-off-the-land attacks.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/bf428f06fa61ce6a2b3fbf7c4f61b16e3b264f55/mini-project-03/screenshots/Screenshot%202026-03-26%20120511.png)

---

### 8. Install Atomic Red Team on the VM

Installed Atomic Red Team on the Windows 11 VM to simulate real-world attack techniques for testing the ASR policy and Defender for Endpoint detections.

Before installation, excluded the C: drive from Windows Security to allow the Atomic Red Team files to be downloaded without being blocked by the antivirus. 

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/bee694d548baefaf3440e8ff278312c34d9eb08e/mini-project-03/screenshots/Screenshot%202026-03-27%20124656.png)

Then installed Atomic Red Team using PowerShell with the following commands:
```
1. Install-Module -Name invoke-atomicredteam,powershell-yaml -Scope CurrentUser

2. IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' -UseBasicParsing); Install-AtomicRedTeam -getAtomics

```
---

### 9. Invoke T1547.001 and Observe Alert in Defender

Invoked MITRE ATT&CK technique T1547.001 (Boot or Logon Autostart Execution: Registry Run Keys / Startup Folder) using Atomic Red Team on the Windows 11 VM. This technique simulates an attacker achieving persistence by adding entries to registry run keys. The following command was used:
```
Invoke-AtomicTest T1547.001
```
![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/36bdc178bf7c4bae9dcdab8ac56b1ad5697128f8/mini-project-03/screenshots/Screenshot%202026-03-27%20130820.png)

The execution successfully triggered alerts in Microsoft Defender for Endpoint, confirming that the endpoint is actively monitoring for and detecting persistence techniques.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/395ed99b2988fe641f9349db6b1c45158794aa02/mini-project-03/screenshots/Screenshot%202026-03-27%20131626.png)

---

## Key Takeaways

- Enabling the Microsoft Intune connection in Defender for Endpoint is essential for unified endpoint security because without it, the two tools cannot share device information or enforce policies together.
- The onboarding package is what connects an endpoint to Defender for Endpoint and once run, the device immediately begins sending telemetry to the Defender portal.
- ASR rules are a powerful way to block known attack techniques at the endpoint level before they can execute, reducing reliance on detection after the fact.
- Excluding a drive from Windows Security before installing Atomic Red Team highlights how attackers use exclusions to bypass antivirus.
- Atomic Red Team allows SOC analysts to safely simulate MITRE ATT&CK techniques and validate whether detections are working as expected.
- T1547.001 triggered alerts in Defender for Endpoint, confirming that persistence techniques are being actively monitored on the onboarded endpoint.

---
## Findings & Incident Report

After running Atomic Red Team simulations, I investigated one of the alerts generated in the Defender portal, following a standard SOC analyst investigation workflow from alert triage to documented findings.

[📄 View Incident Report](INCIDENT-REPORT.md)

## What's Next

**Mini Project 04** — Identity protection and Conditional Access policy configuration using Microsoft Entra ID.

---

*Part of the [Azure-Sentinel-XDR-Labs](../README.md) project series.*



## Table of Contents

1. [Create a Windows 11 VM in VMware Workstation Pro](#1-create-a-windows-11-vm-in-vmware-workstation-pro)
2. [Configure Advanced Features in Microsoft Defender](#2-configure-advanced-features-in-microsoft-defender)
3. [Onboard the VM to Microsoft Defender for Endpoint](#3-onboard-the-vm-to-microsoft-defender-for-endpoint)
4.  [Run the Onboarding Package](#4-run-the-onboarding-package)
5. [Run a Phishing Email Test on User Account](#5-run-a-phishing-email-test-on-user-account)
6. [Launch a Phishing Simulation from Microsoft Defender](#6-launch-a-phishing-simulation-from-microsoft-defender)
7. [Click the Phishing Link as the Target User](#7-click-the-phishing-link-as-the-target-user)
8. [Review the Phishing Simulation Report and URL Click Activity](#8-review-the-phishing-simulation-report-and-url-click-activity)
---

## Steps

### 1. Create a Windows 11 VM in VMware Workstation Pro

Created a Windows 11 virtual machine using VMware Workstation Pro to act as the test endpoint for this lab. This VM will be onboarded to Microsoft Defender for Endpoint and managed through Microsoft Intune, simulating a real-world enterprise endpoint environment.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/a782402c1c07a7c8bbbc98f027a35c8647ceaa23/mini-project-03/screenshots/Screenshot%202026-03-26%20111043.png)

---

### 2. Configure Advanced Features in Microsoft Defender

Navigated to Settings → Endpoints → Advanced Features in the Microsoft Defender XDR portal and enabled the following settings before onboarding the endpoint:

#### EDR in Block Mode — allows Defender for Endpoint to block malicious artifacts even when a third-party antivirus is the primary solution.
#### Custom Network Indicators — enables the use of custom IP, URL, and domain indicators for threat detection and blocking.
#### Web Content Filtering — allows monitoring and blocking of websites based on content categories.
#### Microsoft Intune Connection — links Defender for Endpoint with Intune to enable unified endpoint security and compliance management.

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

### 5. Run a Phishing Email Test on User Account

Sent a simulated phishing email to Bob's account to test the effectiveness of the policies applied. The email was automatically directed to the junk folder rather than the inbox, with a notification warning that the sender is not frequently contacted. This confirms that the anti-phishing and Safe Links policies are working as intended

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/42faf917995624589b34e7f96349405d1b76da9a/mini-project-02/screenshots/Screenshot%202026-03-22%20151446.png)


---

### 6. Launch a Phishing Simulation from Microsoft Defender

Launched a phishing simulation using the Attack Simulation Training feature in the Microsoft Defender XDR portal. The simulation sent a realistic phishing email to the test users to evaluate how they respond to a real-world phishing attempt

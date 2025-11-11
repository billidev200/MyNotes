---
icon: windows
---

# Microsoft Windows Hardening

<figure><img src="../../.gitbook/assets/dbbd403c6b1196904312c7b88f2514f2.png" alt=""><figcaption></figcaption></figure>

## Updating Windows

Update windows AVOID Legacy&#x20;

## Storage Management

**Data Encryption Through BitLocker**\
Encryption of the computer is one of the most vital things to which we usually pay little attention. The worst nightmare is that someone gets unfettered access to your devices' data. Encryption ensures that you or someone you share the recovery key with can access the stored content.

## **Windows Sandbox**

To run applications safely, we can use a temporary, isolated, lightweight desktop environment called Windows Sandbox. We can install software inside this safe environment, and this software will not be a part of our host machine, it will remain sandboxed. Once the Windows Sandbox is closed, everything, including files, software, and states will be deleted. We would require Virtualisation enabled on our OS to run this feature. We cannot try this in the attached VM but the steps for enabling the Sandbox feature are as below:`Click Start > Search for 'Windows Features' and turn it on > Select Sandbox > Click OK to restart`&#x20;

## **Windows Secure Boot**

Secure boot – an advanced security standard - checks that your system is running on trusted hardware and firmware before booting, which ensures that your system boots up safely while preventing unauthorised software access from taking control of your PC, like malware.\
You are already in a secure boot environment if you run a modern PC with Unified Extensible Firmware Interface UEFI (the best replacement for BIOS) or Windows 10. You can check the status of the secure boot by following:

<figure><img src="../../.gitbook/assets/7e86a928fcad06fc3a30d1e69620fa45.png" alt=""><figcaption></figcaption></figure>

## Windows Defender Firewall

Windows Defender Firewall is a built-in application that protects computers from malicious attacks and blocks unauthorised traffic through inbound and outbound rules or filters

## Disable unused Networking Devices

<figure><img src="../../.gitbook/assets/381409d62e6ebaf2c542849dc941f58c.png" alt=""><figcaption></figcaption></figure>

## Disable SMB protocol        &#x20;

```
user@machine$ Disable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
Path          :
Online        : True
RestartNeeded : False

```

## Preventing Remote Access to Machine

<figure><img src="../../.gitbook/assets/340bfd9d93e9a44e2f244fc1d2d302ea.png" alt=""><figcaption></figcaption></figure>

## Mitigating Address Resolution Protocol Attack

## Microsoft Office Hardening

Microsoft Office Suite is one of the most widely used application suites in all sectors, including financial, telecom, education, etc. Malicious actors abuse its functionality through macros, Flash applets, object linking etc., to achieve Remote Code Execution. Hardening of Microsoft Office may vary from person to person as legitimate functionality of Microsoft Office is exploited to gain access. For example, disabling macros in a University may be helpful as no one uses it; however, banks cannot disable macros as they heavily rely on complex invoices and formulas through macros. The attached VM contains a batch file based on best practices and [Microsoft Attack Surface Reduction Rules](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference?view=o365-worldwide) for hardening Microsoft Office. To execute the script, right-click on the file office.bat on Desktop and Run as Administrator.

## AppLocker

AppLocker is a recently introduced feature that allows users to block specific executables, scripts, and installers from execution through a set of rules. We can easily configure them on a single PC or network through a GUI by the following method:

<figure><img src="../../.gitbook/assets/7809f59c32041093a48fb49e3dea1891.png" alt=""><figcaption></figcaption></figure>

## Protecting the Browser through Microsoft Smart Screen

Microsoft SmartScreen helps to protect you from phishing/malware sites and software when using Microsoft Edge. It helps to make informed decisions for downloads and lets you browse safely in Microsoft Edge by:

* Displaying an alert if you are visiting any suspicious web pages.
* Vetting downloads by checking their hash, signature etc against a malicious software database.
* Protecting against phishing and malicious sites by checking visited websites against a threat intelligence database.

## Identity & Access Management

**Standard vs Admin Account**

Identity and access management involves employing best practices to ensure that only authenticated and authorised users can access the system. There are two types of accounts in Windows, i.e. Admin and Standard Account. Per best practice, the Admin account should only be used to carry out tasks like software installation and accessing the registry editor, service panel, etc. Routine functions like access to regular applications, including Microsoft Office, browser, etc., can be allowed to standard accounts.

**User Account Control (UAC)**

<figure><img src="../../.gitbook/assets/5e5609be5a55c30aa42a27801c5362c4.png" alt=""><figcaption></figcaption></figure>

**Local Policy and Group Policies Editor**

Group Policy Editor is a built-in interactive tool by Microsoft that allows to configure and implement local and group policies. We mainly use this feature when part of a network; however, we can also use it for a workstation to limit the execution of vulnerable extensions, set password policies, and other administrative settings.\
Note: The feature is not available in Windows Home but only in the Pro and Enterprise versions

1. Setting A Lockout Policy
2. Windows hardening policies cheat sheet

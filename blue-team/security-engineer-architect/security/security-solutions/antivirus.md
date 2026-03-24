---
icon: virus-covid
---

# Antivirus

Antivirus software also known as anti-malware, is mainly used to monitor, detect, and prevent malicious software from being executed within the host.  Most antivirus software applications use well-known features, including Background scanning, Full system scans, Virus definitions. In the background scanning, the antivirus software works in real-time and scans all open and used files in the background. The full system scan is essential when you first install the antivirus. The most interesting part is the virus definitions, where antivirus software replies to the pre-defined virus. That's why antivirus software needs to update from time to time.

## Detection techniques

There are various detection techniques that the antivirus uses, including:

* Signature-based detection
* Heuristic-based detection
* Behavior-based detection

**Signature-based detection** is one of the common and traditional techniques used in antivirus software to identify malicious files. Often, researchers or users submit their infected files into an antivirus engine platform for further analysis by AV vendors, and if it confirms as malicious, then the signature gets registered in their database. The antivirus software compares the scanned file with a database of known signatures for possible attacks and malware on the client-side. If we have a match, then it considers a threat.

**Heuristic-based** **detection** uses machine learning to decide whether we have the malicious file or not. It scans and statically analyses in real-time in order to find suspicious properties in the application's code or check whether it uses uncommon Windows or system APIs. It does not rely on the signature-based attack in making the decisions, or sometimes it does. This depends on the implementation of the antivirus software.

Finally, **Behavior-based detection** relies on monitoring and examining the execution of applications to find abnormal behaviors and uncommon activities, such as creating/updating values in registry keys, killing/creating processes, etc.

## **Antivirus Engines**

An AV engine is responsible for finding and removing malicious code and files. Good AV software implements an effective and solid AV core that accurately and quickly analyzes malicious files. Also, It should handle and support various file types, including archive files, where it can self-extract and inspect all compressed files.

Most AV products share the same common features but are implemented  differently, including but not limited to:

* Scanner
* Detection techniques
* Compressors and Archives
* Unpackers
* Emulators

### **Scanner**

The scanner feature is included in most AV products: AV software runs and scans in real-time or on-demand. This feature is available in the GUI or through the command prompt. The user can use it whenever required to check files or directories. The scanning feature must support the most known malicious file types to detect and remove the threat. In addition, it also may support other types of scanning depending on the AV software, including vulnerabilities, emails, Windows memory, and Windows Registry.

### **Compressors and Archives**

The "Compressors and Archives" feature should be included in any AV software. It must support and be able to deal with various system file types, including compressed or archived files: ZIP, TGZ, 7z, XAR, RAR, etc. Malicious code often tries to evade host-based security solutions by hiding in compressed files. For this reason, AV software must decompress and scan through all files before a user opens a file within the archive.

### PE (Portable Executable) Parsing and Unpackers

Malware hides and packs its malicious code by compressing and encrypting it within a payload. It decompresses and decrypts itself during runtime to make it harder to perform static analysis. Thus, AV software must be able to detect and unpack most of the known packers (UPX, Armadillo, ASPack, etc.) before the runtime for static analysis.

Malware developers use various techniques, such as Packing, to shrink the size and change the malicious file's structure. Packing compresses the original executable file to make it harder to analyze. Therefore, AV software must have an unpacker feature to unpack protected or compressed executable files into the original code.

Another feature that AV software must have is Windows Portable Executable (PE) header parser. Parsing PE of executable files helps distinguish malicious and legitimate software (.exe files). The PE file format in Windows (32 and 64 bits) contains various information and resources, such as object code, DLLs, icon files, font files, and core dumps.

### Emulators

An emulator is an Antivirus feature that does further analysis on suspicious files. Once an emulator receives a request, the emulator runs the suspect (exe, DLL, PDF, etc.) files in a virtualized and controlled environment. It monitors the executable files' behavior during the execution, including the Windows APIs calls, Registry, and other Windows files. The following are examples of the artifacts that the emulator may collect:

* API calls
* Memory dumps
* Filesystem modifications
* Log events
* Running processes
* Web requests

{% hint style="info" %}
An emulator stops the execution of a file when enough artifacts are collected to detect malware.
{% endhint %}

**Other common features**

The following are some common features found in AV products:

* A self-protection driver to guard against malware attacking the actual AV.
* Firewall and network inspection functionality.
* Command-line and graphical interface tools.
* A daemon or service.
* A management console.

{% hint style="info" %}
A daemon is a computer program that runs as a background process rather than under direct user control, handling tasks like system maintenance, networking, or printing
{% endhint %}

## Static Detection

![Static detection flow](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/06689aaadc7842fbe0cc1424e89e1b3c.png)

A static detection technique is the simplest type of Antivirus detection, which is based on predefined signatures of malicious files. Simply, it uses pattern-matching techniques in the detection, such as finding a unique string, CRC (Checksums), sequence of bytecode/Hex values, and Cryptographic hashes (MD5, SHA1, etc.).

It then performs a set of comparisons between existing files within the operating system and a database of signatures. If the signature exists in the database, then it is considered malicious. This method is effective against static malware.

### Yara Rules for Static Detection

<figure><img src="../../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

One of the tools that help in static detection is [Yara(opens in new tab)](http://virustotal.github.io/yara/). Yara is a tool that allows malware engineers to classify and detect malware. Yara uses rule-based detection, so in order to detect new malware, we need to create a new rule.&#x20;

YARA is a tool aimed at (but not limited to) helping malware researchers to identify and classify malware samples. With YARA you can create descriptions of malware families (or whatever you want to describe) based on textual or binary patterns. Each description, a.k.a rule, consists of a set of strings and a boolean expression which determine its logic. Let's see an example:

```
rule silent_banker : banker
{
    meta:
        description = "This is just an example"
        threat_level = 3
        in_the_wild = true

    strings:
        $a = {6A 40 68 00 30 00 00 6A 14 8D 91}
        $b = {8D 4D B0 2B C1 83 C0 27 99 6A 4E 59 F7 F9}
        $c = "UVODFRYSIHLNWPEJXQZAKCBGMT"

    condition:
        $a or $b or $c
}
```

## Dynamic Detection

The dynamic detection approach is advanced and more complicated than static detection. Dynamic detection is focused more on checking files at runtime using different methods. The following diagram shows the dynamic detection scanning flow:

<figure><img src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/5d0d8cd90a2c4b2ce035af1f3b735563.png" alt=""><figcaption></figcaption></figure>

The first method is by monitoring Windows APIs. The detection engine inspects Windows application calls and monitors Windows API calls using Windows [Hooks(opens in new tab)](https://docs.microsoft.com/en-us/windows/win32/winmsg/about-hooks).

Another method for dynamic detection is Sandboxing. A sandbox is a virtualized environment used to **run malicious files separated from the host computer. This is usually done in an isolated environment, and the primary goal is to analyze how the malicious software acts in the system**. Once the malicious software is confirmed, a unique signature and rule will be created based on the characteristic of the binary. Finally, a new update will be pushed into the cloud database for future use.

This type of detection also has drawbacks because it requires executing and running the malicious software for a limited time in the virtual environment to protect the system resources. As with other detection techniques, dynamic detection can be bypassed. Malware developers implement their software to not work within the virtual or simulated environment to avoid dynamic analysis. For example, **they check if the system spawns a real process of executing the software before running** **malicious activities or let the software wait sometime before execution.**

## Heuristic and Behavioral Detection

Heuristic and behavioral detection have become essential in today's modern AV products. Modern AV software relies on this type of detection to detect malicious software. The heuristic analysis uses various techniques, including static and dynamic heuristic methods:

1. Static Heuristic Analysis is a process of decompiling (if possible) and extracting the source code of the malicious software. Then, the extracted source code is compared to other well-known virus source codes. These source codes are previously known and predefined in a heuristic database. If a match meets or exceeds a threshold percentage, the code is flagged as malicious.
2. Dynamic Heuristic Analysis is based on predefined behavioral rules. Security researchers analyzed suspicious software in isolated and secured environments. Based on their findings, they flagged the software as malicious. Then, behavioral rules are created to match the software's malicious activities within a target machine.

The following are examples of behavioral rules:&#x20;

* If a process tries to interact with the LSASS.exe process that contains users' NTLM hashes, Kerberos tickets, and more
* If a process opens a listening port and waits to receive commands from a Command and Control (C2) server

The following diagram shows the Heuristic and behavioral detection scanning flow:

![Heuristic and behavioral detection flow](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/bbdeb1fd3e1140a20ebee8553b194054.png)

## ClamAV

<figure><img src="../../../../.gitbook/assets/image (33).png" alt="" width="229"><figcaption></figcaption></figure>

{% embed url="https://www.clamav.net/" %}

{% embed url="https://www.virustotal.com/gui/" %}

## Fingerprinting AV software

As a red teamer, we do not know what AV software is in place once we gain initial access to a target machine. Therefore, it is important to find and identify what host-based security products are installed, including AV software. AV fingerprinting is an essential process to determine which AV vendor is present. Knowing which AV software is installed is also quite helpful in creating the same environment to test bypass techniques. &#x20;

This section introduces different ways to look at and identify antivirus software based on static artifacts, including service names, process names, domain names, registry keys, and filesystems.

The following table contains well-known and commonly used AV software.&#x20;

| Antivirus Name     | Service Name                      | Process Name                       |
| ------------------ | --------------------------------- | ---------------------------------- |
| Microsoft Defender | WinDefend                         | MSMpEng.exe                        |
| Trend Micro        | TMBMSRV                           | <p>TMBMSRV.exe<br></p>             |
| Avira              | AntivirService, Avira.ServiceHost | avguard.exe, Avira.ServiceHost.exe |
| Bitdefender        | VSSERV                            | bdagent.exe, vsserv.exe            |
| Kaspersky          | AVP\<Version #>                   | <p>avp.exe, ksde.exe<br></p>       |
| AVG                | AVG Antivirus                     | AVGSvc.exe                         |
| Norton             | Norton Security                   | NortonSecurity.exe                 |
| McAfee             | McAPExe, Mfemms                   | MCAPExe.exe, mfemms.exe            |
| Panda              | PavPrSvr                          | PavPrSvr.exe                       |
| Avast              | Avast Antivirus                   | afwServ.exe, AvastSvc.exe          |

One way to fingerprint AV is by using public tools such as [SharpEDRChecker(opens in new tab)](https://github.com/PwnDexter/SharpEDRChecker). It is written in C# and performs various checks on a target machine, including checks for AV software, like running processes, files' metadata, loaded DLL files, Registry keys, services, directories, and files.

We have pre-downloaded the SharpEDRChecker from the [GitHub repo(opens in new tab)](https://github.com/PwnDexter/SharpEDRChecker) so that we can use it in the attached VM. Now we need to compile the project, and we have already created a shortcut to the project on the desktop (SharpEDRChecker). To do so, double-click on it to open it in Microsoft Visual Studio 2022. Now that we have our project ready, we need to compile it, as shown in the following screenshot:

<figure><img src="../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

C# Fingerprint checks

Another way to enumerate AV software is by coding our own program. We have prepared a C# program in the provided Windows 10 Pro VM, so we can do some hands-on experiments! You can find the project's icon on the desktop (AV-Check) and double-click it to open it using Microsoft Visual Studio 2022.

The following C# code is straightforward, and its primary goal is to determine whether AV software is installed based on a predefined list of well-known AV applications.

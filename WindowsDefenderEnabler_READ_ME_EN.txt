Tool name: WindowsDefenderEnabler.exe

Version: 1.0
SHA256 checksum: 721B6CC43875DA7C06BADB62876519921258A0B4C7F774D62272209F24DB5D9F
File Size: 14,5 KB
Written in C# (based on the .NET Framework 4.x).
Compiled into an .exe executable file with an MZ file header.

Author: Michał Sołtysik
Cybersecurity Analyst & Consultant | Forensics Examiner | SOC Trainer | Cyber Warfare Organizer
Official website: https://michalsoltysik.com/
LinkedIn: https://www.linkedin.com/in/michal-soltysik-ssh-soc/
Cybersecurity content: https://www.youtube.com/playlist?list=PL0RdRWQWldOAAKBqOVEutxKMP-a6CNoLY
Accredible: https://www.credential.net/profile/michalsoltysik/wallet
Credly: https://www.credly.com/users/michal-soltysik
Email: me@michalsoltysik.com

Purpose: A Windows tool designed for SOC labs and controlled test environments, for enabling 16 Windows Defender components (9 functional protection components and 7 services/drivers) to support malware research, detection engineering, and blue team training.
License: Free for personal and commercial use.

The application performs the following functions:

(1) runs as a Windows utility intended for restoring Windows Defender functionality in lab environments and requires administrator privileges;
(2) removes policy-level registry values used to disable Defender functional protection components;
(3) restores startup configuration for Defender-related services and drivers, re-enabling them to their default automatic state;
(4) deletes the scheduled task responsible for enforcing Defender disable persistence;
(5) appends a single timestamped entry per execution to the same shared log file used by the disabler, explicitly recording that Windows Defender was enabled and maintaining continuity of auditing;
(6) displays an informational pop-up notification only when the disabling scheduled task existed and was successfully removed.

Details - Defender components affected:

| #  | Defender component / service / driver  | Type                        | Effect                                                   |
| -- | -------------------------------------- | --------------------------- | -------------------------------------------------------- |
| 1  | Antivirus / Antispyware core           | Functional protection       | Master policy kill switches for Defender AV              |
| 2  | PUA / PUP detection                    | Functional protection       | Disables potentially unwanted application detection      |
| 3  | Real-time protection                   | Functional protection       | Disables core real-time scanning engine                  |
| 4  | Behavior monitoring                    | Functional protection       | Disables behavioral analysis engine                      |
| 5  | On-access scanning                     | Functional protection       | Disables file open/write scanning                        |
| 6  | IOAV scanning                          | Functional protection       | Disables download and attachment scanning                |
| 7  | Cloud-delivered protection and samples | Functional protection       | Disables cloud backend and sample submission             |
| 8  | Exploit Guard                          | Functional protection       | Disables Controlled Folder Access and Network Protection |
| 9  | Scan engine hardening                  | Functional protection       | Weakens scan depth and engine hardening                  |
| 10 | WinDefend                              | Service (user mode)         | Main Defender antivirus service                          |
| 11 | WdBoot                                 | Driver (boot start)         | Loads Defender components during system boot             |
| 12 | WdFilter                               | Driver (file system filter) | File system minifilter intercepting file operations      |
| 13 | WdNisDrv                               | Driver (kernel mode)        | Network Inspection System kernel driver                  |
| 14 | WdNisSvc                               | Service (user mode)         | Network Inspection System service                        |
| 15 | SecurityHealthService                  | Service (platform / UI)     | Windows Security health monitoring and reporting         |
| 16 | Sense                                  | Service (EDR sensor)        | Defender for Endpoint (EDR) sensor                       |

Operational effect:

The table above documents all Windows Defender functional components, services, and drivers affected by registry and service-level enforcement; this tool removes or restores these settings to re-enable Windows Defender functionality.
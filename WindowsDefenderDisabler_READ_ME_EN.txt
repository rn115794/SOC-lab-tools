Tool name: WindowsDefenderDisabler.exe

Version: 1.0
SHA256 checksum: C5C47EE71A2E5709A1CB4E470A909572D557B161A507EDAD7F022E49D70B3376
File Size: 44,5 KB
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

Purpose: A Windows tool designed for SOC labs and controlled test environments, for disabling 16 Windows Defender components (9 functional protection components and 7 services/drivers) to support malware research, detection engineering, and blue team training.
License: Free for personal and commercial use.

Important notice:

(1) This tool modifies security-critical Windows Defender configuration by applying registry- and service-level enforcement intended exclusively for isolated SOC labs and controlled test environments.
(2) Improper use in a production environment, enterprise network, or unmanaged system may significantly reduce system security, expose the host to malware, or violate organizational security policies.
(3) Execution of this tool must be explicitly approved by the system owner or an authorized administrator. Use on systems without proper authorization or outside of controlled testing scenarios is strongly discouraged.
(4) Operation of this tool requires full understanding of its impact and full responsibility for its use.
(5) This tool must never be deployed on production systems, end-user workstations, or environments where security controls are required to remain active.

The application performs the following functions:

(1) runs as a Windows utility intended for isolated lab environments and requires administrator privileges;
(2) disables Windows Defender by applying policy-level registry changes affecting 9 functional protection components, including real-time monitoring, behavior monitoring, cloud reporting, scanning features, and exploit guard controls;
(3) disables 7 Defender-related services and drivers by modifying their startup configuration at the system level;
(4) ensures persistence of the disabled state by creating and executing a scheduled task running as SYSTEM with multiple triggers, including system boot, user logon, and periodic execution, to ensure Windows Defender remains disabled and does not automatically re-enable itself over time;
(5) copies itself to a fixed system location and executes from there to ensure consistent task execution;
(6) appends a single timestamped entry on each execution, including executions at system boot, at user logon, and multiple times per day (separate time triggers - effectively hourly), to a shared log file, recording Windows Defender disable operations and providing a simple audit trail;
(7) displays an informational pop-up notification only on first execution when the scheduled task is created.

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

The table above documents all Windows Defender functional components, services, and drivers affected by registry and service-level enforcement; this tool applies these settings to disable protection and to ensure Windows Defender does not automatically re-enable itself over time.
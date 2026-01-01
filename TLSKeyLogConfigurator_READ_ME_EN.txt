Tool name: TLSKeyLogConfigurator.exe

Version: 1.0
SHA256 checksum: FF0F128CE4E06ABAD6BF8820A269581275699FDC0E68779A6786141CDFA81D0A
File Size: 39 KB
Written in PowerShell, executed within the .NET-based Windows PowerShell runtime.
Compiled into an .exe executable file with an MZ file header.

Author: Michał Sołtysik
Cybersecurity Analyst & Consultant | Forensics Examiner | SOC Trainer | Cyber Warfare Organizer
Official website: https://michalsoltysik.com/
LinkedIn: https://www.linkedin.com/in/michal-soltysik-ssh-soc/
Cybersecurity content: https://www.youtube.com/playlist?list=PL0RdRWQWldOAAKBqOVEutxKMP-a6CNoLY
Accredible: https://www.credential.net/profile/michalsoltysik/wallet
Credly: https://www.credly.com/users/michal-soltysik
Email: me@michalsoltysik.com

Purpose: A Windows tool designed for SOC labs and controlled test environments, providing automated TLS key logging setup for encrypted web traffic analysis.
License: Free for personal and commercial use.

Important notice:

(1) This tool configures TLS key logging and Wireshark preferences, enabling decryption and inspection of encrypted web traffic for analysis purposes.
(2) When misused, TLS key logging may allow sensitive or private communications to be decrypted and inspected, potentially violating privacy, confidentiality, or organizational security policies.
(3) Execution of this tool must be explicitly approved by the system owner or an authorized administrator, and its use must comply with applicable laws, internal policies, and scope of authorization.
(4) This tool is intended exclusively for SOC labs, controlled test environments, and authorized forensic or training scenarios.
(5) Operation of this tool requires full understanding of its impact and full responsibility for its use, particularly when handling decrypted network traffic.

Prerequisite:

(1) Wireshark must be installed on the system for TLS traffic decryption to be usable; the tool configures TLS key logging and Wireshark preferences but does not install Wireshark itself.

The application performs the following functions:

(1) runs as a console application that performs user-level TLS key logging configuration and Wireshark preference updates; it is recommended to run the tool as an administrator to ensure successful execution policy adjustment for the current process;
(2) automates the setup of TLS key logging on Windows by creating a dedicated key log directory and file and configuring the SSLKEYLOGFILE user environment variable;
(3) updates Wireshark preferences to enable TLS session decryption using the configured key log file;
(4) provides a detailed status view showing Wireshark installation detection, key log file existence and size (bytes, KB, MB), environment variable state (user and session), and Wireshark TLS configuration status;
(5) supports safe configuration (no overwrite) and forced configuration modes, with optional backup creation of existing key log files and graceful handling of locked files;
(6) logs all actions to a transcript file stored on the user's desktop, enabling auditing and repeatability in forensic and SOC training environments.
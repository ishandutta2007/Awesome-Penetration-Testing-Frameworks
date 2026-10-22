# Awesome-Penetration-Testing-Frameworks

## Top Penetration Testing Frameworks Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Post-Exploitation, Adversary Simulation & Command-and-Control*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Penetration Testing Frameworks**. These tools provide the infrastructure for authorized adversary simulation — exploit delivery, payload generation, session management, and command-and-control (C2) — used by red teams to validate detection and response capabilities.

**Examples** include Metasploit Framework, Sliver, Mythic, Havoc, Empire, Covenant, Cobalt Strike, Core Impact, Immunity CANVAS, and Brute Ratel (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, modular C2 architecture, and transparent implant behavior — ideal for red teams conducting authorized engagements who need reproducible tradecraft without commercial licensing.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Cobalt Strike](https://www.cobaltstrike.com/)**  
  **The commercial standard for adversary simulation and red team operations** — a threat emulation tool that simulates adversarial post-exploitation scenarios using Beacon (post-exploitation agent) and Malleable C2 (command-and-control program enabling modification of network indicators to blend with traffic) . Features post-exploitation (PowerShell execution, keystroke logging, screenshots, file download, payload spawning), browser pivoting to bypass two-factor authentication, shared sessions for collaborative engagements, and reporting/logging . Available individually or bundled with Core Impact and Outflank Security Tooling (OST) . **Best for red teams needing a mature, commercially supported C2** with extensive community tooling.

- **[Core Impact](https://www.coresecurity.com/)**  
  **Advanced penetration testing tool mirroring adversarial mindset across four dimensions**: automation (wizards for repeatable results), exploit library (expansive multi-platform commercial-grade exploits regularly updated), centralization (unified environment from information gathering to reporting with retesting/remediation validation), and multi-vector testing (network, client-side, web application with seamless pivoting) . **Core Security also maintains Impacket**, the open-source Python library for network protocols (SMB1-3, MSRPC) . **Best for enterprises wanting a battle-tested commercial platform** with automated exploitation and comprehensive reporting.

- **[Immunity CANVAS](https://www.immunityinc.com/)**  
  **Commercial exploitation platform with 800+ exploits** and monthly updates averaging 4 new exploits . **Prioritizes high-value vulnerabilities** — remote, unauthenticated flaws in mainstream software . **Supports third-party exploit packs** including DSquare's D2 Exploitation Pack, Intevydis's VulnDisco, and Gleg's Agora and SCADA . **Cross-platform** (Windows, Linux, macOS, plus command-line for mobile and commercial Unix) . **Best for penetration testers wanting a broad exploit library** with third-party pack extensibility.

- **[Brute Ratel C4](https://bruteratel.com/)**  
  **Commercial adversary simulation framework** active since 2020, priced at **$2,500/year** . Features **Badger payloads**, **EDR evasion**, and **syscall-only** execution . **Note**: cracked copies have been abused by ALPHV/BlackCat ransomware, making it a monitored threat in the wild . **Best for advanced red teams** needing a commercial C2 with EDR evasion focus.

## Open-Source GitHub Projects

- **[Metasploit Framework](https://github.com/rapid7/metasploit-framework)**  
  **The world's most used penetration testing framework** — BSD-style licensed. **Module types**: exploit (target specific vulnerabilities), payload (code executed after exploitation), auxiliary (scanning/fuzzing/enumeration), post-exploitation (actions after compromise), encoder (obfuscate payloads), NOPs (buffer overflow padding), and evasion (bypass security controls) . **Meterpreter** provides an advanced post-exploitation agent with system info, file operations, process migration, networking, and port forwarding . **Workflow**: `search eternalblue` → `use exploit/windows/smb/ms17_010_eternalblue` → `set RHOSTS` → `set PAYLOAD` → `exploit` . **Commercial Pro edition** adds `pro_discover`, `pro_exploit` (multi-host automated exploitation), `pro_bruteforce` (smart password auditing), `pro_collect` (automated evidence gathering), and one-click reporting . **Best for any authorized penetration test** — the foundational framework every tester learns.

- **[Sliver](https://github.com/BishopFox/sliver)**  
  **The leading open-source general-purpose C2 framework** from Bishop Fox. **Implant generation** with `sliver > generate --http https://... --os windows --arch amd64` . **Implants are larger (15-35 MB)** because Go compiles a fully self-contained binary with runtime and dependencies statically linked — no external DLL dependencies or runtime install required on target . **Multiple protocols**: HTTP(S), mTLS, DNS, WireGuard, and TCP . **mTLS-secured C2 communication** over port 443 . **Session management** with `sessions`, `use [SESSION_ID]`, `whoami`, and `ps` without requiring a shell . **Best for red teams wanting a modern, actively maintained open-source C2** with cross-platform implants.

- **[Mythic](https://github.com/its-a-feature/Mythic)**  
  **The modular, cross-platform C2 framework with web-based UI** — open-source alternative to Cobalt Strike . **Supports multiple agent types** installed as Docker containers: Medusa (Python 2.7/3.8), Hannibal (PIC C), Thanatos (Rust, Linux/Windows), Poseidon (Golang, Linux/macOS), Apollo (C# .NET 4.0), Athena (.NET), and Xenon (C, httpx-compatible) . **Transport profiles** include HTTP, httpx, WebSocket, DNS, dynamic HTTP, SMB, and TCP . **Agent protocol library** in Rust with AES-256-CBC-HMAC encryption, RSA key exchange, and transport abstraction . **Best for teams wanting a flexible, plugin-based C2** with diverse agent and transport options.

- **[Havoc](https://github.com/HavocFramework/Havoc)**  
  **Modern and malleable post-exploitation C2 framework** by C5pider — client written in C++/Qt with a modern Dracula-based dark theme, teamserver in Golang . **Demon agent** written in C and ASM with **sleep obfuscation via Ekko, Ziliean, or FOLIAGE**, **x64 return address spoofing**, **indirect syscalls for Nt* APIs**, **SMB support**, **token vault**, and **patching AMSI/ETW via hardware breakpoints** . **Payload generation** (exe/shellcode/dll) with HTTP/HTTPS listeners, customizable C2 profiles, and external C2 . **Explicitly designed for malleability and modularity** — not evasive by default, but operators add custom modules for their target's detection system . **Best for operators wanting a modern C2 with fine-grained control** over evasion techniques.

- **[Empire](https://github.com/BC-SECURITY/Empire)**  
  **Post-exploitation and adversary emulation framework** for red teams — Python 3 server with modular design . **Supports PowerShell, Python 3, C#, and IronPython 3 agents** . **HTTP/S, Malleable HTTP, OneDrive, Dropbox, and PHP listeners** . **Massive library (400+) of tools** in PowerShell, C#, and Python including Mimikatz, Seatbelt, Rubeus, SharpSploit, and Certify . **Donut integration** for shellcode generation, **in-memory .NET assembly execution**, **JA3/S and JARM evasion**, and **MITRE ATT&CK integration** . **Starkiller** provides a web application GUI . **Docker, Kali, ParrotOS, Ubuntu, and Debian installation support** . **Best for red teams wanting a modular post-exploitation framework** with a huge built-in tool library.

- **[Covenant](https://github.com/cobbr/Covenant)**  
  **Collaborative .NET C2 framework for red teamers** — provides a **Swagger-documented REST API** for managing listeners, launchers, grunts (agents), and tasks . **Automates Covenant operations through its API** for authorized engagements: creating HTTP/HTTPS listeners, generating binary and PowerShell launchers, deploying grunts, executing tasks on compromised hosts, and tracking lateral movement . **Best for red teams wanting a .NET-focused C2** with API-driven automation.

### Additional Strong Open-Source Options

- **Impacket** — Collection of Python classes for working with network protocols (SMB1-3, MSRPC). Maintained by Core Security. Essential for network protocol exploitation .
- **Donut** — Shellcode generation framework integrated into Empire for converting .NET assemblies into position-independent shellcode.
- **Starkiller** — Web application GUI for PowerShell Empire, packaged as a git submodule with Empire 5.0 .

**Frameworks for building custom systems**: Combine **Metasploit Framework** for the broadest exploit and module library with Meterpreter post-exploitation, **Sliver** for a modern general-purpose C2 with cross-platform Go implants, **Mythic** for modular agent and transport flexibility via Docker-installed plugins, **Havoc** for a malleable C2 with fine-grained evasion control, and **Empire** for post-exploitation with a massive built-in tool library — to build a penetration testing stack tailored to your engagement scope, evasion requirements, and operational security posture.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- **Penetration testing frameworks and C2 tools must only be used against systems you own or have explicit written authorization to test.** Unauthorized access to computer systems is illegal and unethical. **Sliver implants are 15-35 MB** because Go statically links the runtime — larger than alternatives but with no external dependencies . **Havoc is explicitly not designed to be evasive by default** — operators add custom modules for target-specific evasion . **Brute Ratel C4 cracked copies have been abused by ransomware groups**, making the tool a monitored threat . **Cobalt Strike is a commercial product with licensing costs**; open-source alternatives like Sliver and Mythic provide comparable C2 functionality without licensing fees . **Covenant operations should be automated via its API for authorized engagements only** .
- Self-hosted open-source solutions require proper infrastructure isolation (dedicated VPS, aged domains, valid SSL certificates), operational security practices, and engagement scope documentation.

---

**Made for penetration testers, red team operators, and security professionals conducting authorized adversary simulation.**
Let's make penetration testing frameworks more open, modular, and operationally secure.

# 🛡️ Cybersecurity Learning Lab

My hands-on cybersecurity learning journey focused on Linux, SOC,
Blue Team, networking, detection, incident response, and security labs.

> Learning by doing. Investigating before assuming.

---

## 🎯 Goals

- Build strong Linux and networking fundamentals
- Develop SOC / Blue Team investigation skills
- Learn log analysis and detection
- Practice incident response
- Understand offensive security in authorized labs
- Build practical security projects
- Document everything I learn

---

## 🧠 Learning Path

| Stage | Topic | Status |
|---|---|---|
| 01 | Linux Fundamentals | 🟢 Complete |
| 02 | Networking | ⚪ In Progress |
| 03 | SOC Fundamentals | ⚪ Planned |
| 04 | Windows Security | ⚪ Planned |
| 05 | Web Security | ⚪ Planned |
| 06 | Detection Engineering | ⚪ Planned |
| 07 | Incident Response | ⚪ Planned |
| 08 | CTF / Security Labs | ⚪ Ongoing |

---

## 📚 Current Progress

### Day 1 — Linux Fundamentals & SOC Investigation

Covered:

- Linux processes
- PID / PPID
- `/proc`
- Process investigation
- CPU triage
- Users and groups
- UID / GID
- sudo / root
- systemd services
- journalctl
- Authentication log analysis
- NetworkManager investigation
- File descriptors
- TCP/UDP vs Unix sockets
- Process lineage
- Network interfaces

### Investigation Method

Event
  ↓
PID
  ↓
User
  ↓
Parent Process
  ↓
Executable
  ↓
Command Line
  ↓
CWD / FDs
  ↓
Network
  ↓
Context
  ↓
Verdict

🧪 Labs
Hands-on practice is performed only in:
- My own machines
- Local VMs
- Docker labs
- CTF platforms
- TryHackMe
- Hack The Box
- Intentionally vulnerable applications
- Explicitly authorized environments
🛠️ Tools
Linux
- ps
- systemctl
- journalctl
- ss
- ip
- grep
- awk
- sed
Security
- Wireshark
- Nmap
- Burp Suite
- YARA
- Sigma
- SIEM platforms
📈 Progress
I document:
- What I learned
- Commands used
- Investigation methodology
- Lab results
- Mistakes and fixes
- Security observations
- Detection ideas

  ---
  
⚠️ Disclaimer
This repository is for educational and defensive security learning.
All security testing is performed only against systems I own,
local labs, CTF environments, or systems where I have explicit authorization.

---

# 📝 Commit style

Don't make commits like:

```text
update
changes
stuff
final
test

# 🛡️ Cybersecurity Learning Lab

My hands-on cybersecurity learning journey focused on **Linux, SOC, Blue Team, networking, detection engineering, incident response, and security labs**.

> **Learning by doing. Investigating before assuming.**

---

## 🎯 Goals

- Build strong Linux and networking fundamentals
- Develop practical SOC / Blue Team investigation skills
- Learn log analysis and security monitoring
- Practice incident response and investigation workflows
- Understand offensive security in authorized lab environments
- Build practical cybersecurity projects
- Document commands, investigations, mistakes, and lessons learned

---

## 🧠 Learning Path

| Stage | Topic | Status |
|------:|-------|--------|
| 01 | Linux Fundamentals | 🟢 Complete |
| 02 | Networking | 🟡 In Progress |
| 03 | SOC Fundamentals | ⚪ Planned |
| 04 | Windows Security | ⚪ Planned |
| 05 | Web Security | ⚪ Planned |
| 06 | Detection Engineering | ⚪ Planned |
| 07 | Incident Response | ⚪ Planned |
| 08 | CTF / Security Labs | 🟡 Ongoing |

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
- `sudo` / root
- systemd services
- `journalctl`
- Authentication log analysis
- NetworkManager investigation
- File descriptors
- TCP/UDP vs Unix sockets
- Process lineage
- Network interfaces

### Investigation Method

```text
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
CWD / File Descriptors
  ↓
Network Activity
  ↓
Context
  ↓
Verdict
```

---

## 🧪 Labs & Practice

Hands-on security testing is performed only in:

- My own machines
- Local virtual machines
- Docker labs
- CTF platforms
- TryHackMe
- Hack The Box
- Intentionally vulnerable applications
- Explicitly authorized environments

---

## 🛠️ Tools

### Linux & System Investigation

- `ps`
- `systemctl`
- `journalctl`
- `ss`
- `ip`
- `grep`
- `awk`
- `sed`
- `top`
- `pstree`
- `curl`
- `dig`

### Security

- Wireshark
- Nmap
- Burp Suite
- YARA
- Sigma
- SIEM platforms

---

## 📈 Progress Documentation

Each learning stage may document:

- What I learned
- Commands used
- Investigation methodology
- Hands-on labs
- Findings and conclusions
- Mistakes and fixes
- Security observations
- Detection ideas
- Lessons learned
- Next steps

---

## 🔎 Investigation Philosophy

The goal is not to immediately label something as malicious.

I follow an investigation process:

```text
Observe
   ↓
Collect Evidence
   ↓
Investigate
   ↓
Correlate Context
   ↓
Determine Impact
   ↓
Make a Verdict
   ↓
Document Findings
```

> **High CPU, an unusual process, or a warning in a log is an investigation trigger — not automatically proof of compromise.**

---

## ⚠️ Security Disclaimer

This repository is for educational and defensive cybersecurity learning.

All security testing is performed only against:

- Systems I own
- Local laboratory environments
- Virtual machines
- CTF platforms
- Intentionally vulnerable applications
- Systems where I have explicit authorization

No unauthorized systems or networks are targeted.

---

# 📝 Commit Convention

I use descriptive commits so the repository history shows **what changed and why**.

### ❌ Avoid vague commits

```text
update
changes
stuff
final
test
fix
new
work
```

### ✅ Preferred Format

```text
<type>: <short description>
```

### Common Types

| Type | Purpose |
|------|---------|
| `docs` | Documentation or notes |
| `lab` | Hands-on lab work |
| `feat` | New learning material or functionality |
| `fix` | Fix an error or incorrect information |
| `refactor` | Reorganize existing content |
| `chore` | Maintenance or repository changes |
| `research` | Research or investigation notes |

### Examples

```text
docs: add day 1 linux investigation notes
docs: add linux command reference
lab: document process investigation workflow
lab: document NetworkManager investigation
docs: add linux permissions notes
docs: add networking fundamentals
research: document authentication log analysis
feat: add process triage checklist
fix: correct systemd service investigation notes
refactor: reorganize linux fundamentals
chore: update repository structure
```

---

## 📂 Repository Structure

```text
cybersecurity-learning-lab/
│
├── README.md
│
├── 01-linux-fundamentals/
│   ├── README.md
│   ├── notes/
│   ├── commands/
│   └── labs/
│
├── 02-networking/
│   ├── README.md
│   ├── notes/
│   ├── commands/
│   └── labs/
│
├── 03-soc-fundamentals/
│   ├── README.md
│   ├── notes/
│   ├── log-analysis/
│   └── labs/
│
├── 04-windows-security/
│   ├── README.md
│   ├── notes/
│   └── labs/
│
├── 05-web-security/
│   ├── README.md
│   ├── notes/
│   └── labs/
│
├── 06-detection-engineering/
│   ├── README.md
│   ├── sigma/
│   ├── yara/
│   └── detection-notes/
│
├── 07-incident-response/
│   ├── README.md
│   ├── playbooks/
│   └── case-notes/
│
├── 08-tryhackme/
│   ├── README.md
│   └── advent-of-cyber-2025/
│
├── 09-tools/
│   ├── README.md
│   └── cheat-sheets/
│
├── resources/
│   ├── commands.md
│   ├── terminology.md
│   └── useful-resources.md
│
└── progress/
    ├── roadmap.md
    └── progress-log.md
```

---

## 🚀 Learning Principle

This repository is not just a collection of commands.

The focus is on understanding:

**What happened → How to investigate it → What evidence supports the conclusion → What the security impact is.**

> **Learn. Investigate. Document. Improve.**

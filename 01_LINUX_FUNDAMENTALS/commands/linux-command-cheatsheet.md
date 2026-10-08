# Linux Command Cheatsheet

> Commands used during Day 1 Linux and SOC investigation practice.

---

## Filesystem

### `pwd`

Show the current working directory.

```bash
pwd
```

### `ls`

List files and directories.

```bash
ls
ls -l
ls -la
```

- `-l` — detailed listing
- `-a` — include hidden files

### `cd`

Change directory.

```bash
cd /path/to/directory
cd ~
```

### `mkdir`

Create a directory.

```bash
mkdir directory-name
mkdir -p parent/child
```

### `touch`

Create an empty file.

```bash
touch file.txt
```

---

## Users & Identity

### `whoami`

Show the current username.

```bash
whoami
```

### `id`

Display UID, GID, and group membership.

```bash
id
```

### `groups`

Show groups associated with the current user.

```bash
groups
```

### `/etc/passwd`

View local user account information.

```bash
cat /etc/passwd
```

### `/etc/shadow`

Contains password-related account information.

Normally requires elevated privileges:

```bash
sudo cat /etc/shadow
```

Do not expose or publish password hashes.

---

## Processes

### `ps`

Display processes.

```bash
ps
```

### `ps aux`

Display detailed information about running processes.

```bash
ps aux
```

Useful for CPU usage, memory usage, process owner, PID, and command.

### `ps -ef`

Display processes in another detailed format.

```bash
ps -ef
```

### `ps -fp PID`

Inspect one process.

```bash
ps -fp 1234
```

### `ps -o`

Choose specific process fields.

```bash
ps -o pid,ppid,user,%cpu,%mem,cmd -p 1234
```

### `echo $$`

Display the PID of the current shell.

```bash
echo $$
```

### `top`

Interactive process monitoring.

```bash
top
```

### `pstree`

Display processes as a tree.

```bash
pstree
pstree -p
```

Useful for process lineage investigation.

### `kill`

Send a signal to a process.

```bash
kill PID
```

Use carefully. Do not terminate processes simply because they look unfamiliar.

---

## `/proc` Investigation

Linux exposes process information through:

```text
/proc/<PID>/
```

### Process executable

```bash
readlink -f /proc/PID/exe
```

### Process command line

```bash
cat /proc/PID/cmdline | tr '\0' ' '
```

### Process working directory

```bash
ls -l /proc/PID/cwd
```

### Process file descriptors

```bash
ls -l /proc/PID/fd
```

Useful for identifying files, devices, pipes, and sockets.

---

## CPU Triage

Sort processes by CPU usage:

```bash
ps aux --sort=-%cpu
```

Show the top 10:

```bash
ps aux --sort=-%cpu | head -10
```

---

## Logs

### `journalctl`

View systemd journal logs.

```bash
journalctl
```

### Recent logs

```bash
journalctl --no-pager -n 20
```

### Warning logs

```bash
journalctl --no-pager -p warning -n 20
```

### Privileged journal access

```bash
sudo journalctl --no-pager -n 30
```

### Service logs

```bash
sudo journalctl -u NetworkManager --no-pager -n 20
```

### Logs since a time

```bash
sudo journalctl --no-pager -u ssh --since "today"
```

### Authentication-related search

```bash
sudo journalctl --no-pager | grep -Ei 'authentication|failed password|accepted password|sudo|session opened|session closed'
```

### Failed authentication search

```bash
sudo journalctl --no-pager -o short-iso | grep -Ei 'failed password|authentication failure|authentication failed|invalid user'
```

---

## `grep`

Search text.

```bash
grep "pattern" file
grep -i "pattern" file
grep -E "pattern1|pattern2"
grep -Ei "pattern1|pattern2"
```

- `-i` — case-insensitive
- `-E` — extended regular expressions

---

## Pipes

Send output from one command into another.

```bash
ps aux | grep python
```

Example:

```bash
ps aux --sort=-%cpu | head -10
```

Mental model:

```text
Command 1
   ↓
Command 2
   ↓
Command 3
```

---

## `head`

Show the beginning of output.

```bash
head
head -10
```

Example:

```bash
ps aux --sort=-%cpu | head -10
```

---

## `tail`

Show the end of output.

```bash
tail
tail -30
```

Example:

```bash
... | tail -30
```

---

## `tr`

Translate or replace characters.

Used for `/proc` command-line investigation:

```bash
cat /proc/5379/cmdline | tr '\0' ' '
```

This converts null separators into spaces so the command line is readable.

---

## `sudo`

Run a command with elevated privileges.

```bash
sudo command
```

Check sudo permissions:

```bash
sudo -l
```

Verify effective identity:

```bash
sudo whoami
```

Expected output when allowed:

```text
root
```

---

## systemd

### Running services

```bash
systemctl --type=service --state=running
```

### Service status

```bash
systemctl status NetworkManager
sudo systemctl status NetworkManager
```

### Service configuration

```bash
systemctl cat NetworkManager
```

### Check startup status

```bash
systemctl is-enabled NetworkManager
```

---

## Networking

### IP addresses

```bash
ip addr
ip a
```

Useful for identifying interfaces, IPv4/IPv6 addresses, MAC addresses, and interface state.

### Routing table

```bash
ip route
```

### Network connections

```bash
ss
```

### Listening TCP/UDP sockets

```bash
ss -tulpn
```

Options:

- `-t` — TCP
- `-u` — UDP
- `-l` — listening
- `-p` — process information
- `-n` — numeric output

### TCP/UDP process investigation

```bash
ss -tunap
```

### Unix sockets

```bash
ss -xap
```

### Search connections for a PID

```bash
ss -plant | grep PID
```

Example:

```bash
ss -plant | grep 5379
```

---

## DNS

### `dig`

Query DNS information.

```bash
dig example.com
```

---

## HTTP

### `curl`

Inspect HTTP response headers:

```bash
curl -I https://example.com
```

Useful for basic HTTP/HTTPS investigation.

---

# SOC Investigation Workflow

```text
1. Identify the PID
       ↓
2. Identify the user
       ↓
3. Check PPID
       ↓
4. Investigate parent process
       ↓
5. Identify executable
       ↓
6. Inspect command line
       ↓
7. Check working directory
       ↓
8. Inspect file descriptors
       ↓
9. Check network connections
       ↓
10. Review relevant logs
       ↓
11. Correlate context
       ↓
12. Determine verdict
```

> **Investigate before assuming.**

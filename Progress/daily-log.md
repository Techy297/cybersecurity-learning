# Daily Progress Log

---

## 2025-12-25
**Time spent:** 2.5 hours

### What I studied
- Linux permissions (read, write, execute)
- SUID concept and purpose

### What I practiced
- Listed SUID binaries using `find`
- Checked permissions using `ls -l`

### Key understanding
- SUID allows a binary to run with the file owner's privileges, not the user’s

### Confusions / Questions
- Still unclear about when SGID is required on directories

### Next step
- Understand SGID on directories with examples

## 26-12-2025

-**Time spent:** 3 hours

### What I tested
- Created users and groups (useradd , groupadd)
- Create Directory and Change group (mkdir, chgrp)
- Give SGID for Group Inherritance (chmod g+s "Directory Name")
- Create new File as new user (touch file.txt)

### What confused me initially
- The confusion was about access, not creation ownership.

### What finally clicked
- A user can access his own home directory , and create files inside SGID if user is member of authorize group. 

### One mistake I made
- Create directory inside home directory.

### One security insight
- A current user can't see another user home directory and SGID does not grant access; it only enforces group ownership after access is allowed.

### Next step
- Learn about sticky bit concept deeply.

## 27-12-2025

### Topics
- SGID on directories (group inheritance vs permissions)
- Sticky bit behavior and root bypass
- UID 0 and privilege model
- Linux directory structure (/home, /etc, /var, /tmp, /usr)
- Binary files vs scripts

### Key Learnings
- SGID enforces group ownership, not access
- Sticky bit restricts users, not root.
- Wrong directory permissions cause real vulnerabilities
- Binary files execute directly on CPU

### Status
Completed with hands-on testing

29-12-2025 : Rest day — health first. Resume tomorrow.

## 📅 30-12-2025

**Time Spent:** 2.5 hours

**Focus:** Linux filesystem permissions (SGID, Sticky Bit, Inodes)

### 🛠 What I Practiced
- Created shared directories with SGID
- Tested sticky bit behavior on delete/rename
- Compared in-place write vs replace-write
- Observed Vim save behavior (:w vs :wq)

### 🧠 What I Understood
- Directories map filenames to inodes
- Inodes represent the real file and data blocks
- Sticky bit protects directory entries, not file content
- Many editors save by replacing files, not writing in-place

### ❌ Mistakes / Confusions
- Assumed sticky bit makes files write-protected
- Confused file write with file replacement

### ✅ Final Conclusion
Sticky bit blocks delete/rename (file replacement), not file writing.

### ➡️ Next Step
- Resume SUID analysis (/usr/bin/passwd, sudo, pkexec)

### 📅 31-12-2025
**Time Spent:** 3 hour

### 🔧 What I Practiced
- SGID on directories (hands-on lab)
- Group ownership inheritance behavior
- User/group permission testing
- Default permission behavior via umask

### 🧪 Lab Details
- Created users and groups
- Applied SGID (chmod 2770) on a shared directory
- Verified file group inheritance
- Tested access denial for non-group users
- Observed file permissions affected by system umask

### 🧠 Key Learnings
- SGID enforces group ownership inheritance, not permissions
- Write access depends on directory permissions, not SGID alone
- Default file permissions are influenced by umask
- umask can be enforced at PAM level, overriding shell configs

### 🔍 Extra Exploration
- Traced umask enforcement to PAM (pam_umask.so)
- Learned login order and why . bashrc may not apply

### ✅ Status
- SGID lab: Completed
- umask behavior: Understood
- System-level debugging: Improved

### 🧠 One-line Reflection
Today I moved from “using Linux” to understanding how Linux decides.

## 01–05 Jan 2026
**Status:** Inconsistent / Partial execution  
**What I did:** College technical competition prep, light C revision, limited hands-on work  
**What went wrong:** No fixed routine, poor documentation, overthinking & distraction  
**Reality check:** Planning and imagination replaced execution  
**Lesson:** Consistency and logging matter more than intensity  
**Decision:** Reset discipline and resume daily task structure from 06-01-2026

### 06-01-2026

## 1. What did I work on?
- SUID, SGID, and Sticky Bit behavior on directories (tested with two users)
- Analysis of the `sudo` binary and sudo misconfiguration scenarios

---

## 2. Why did I work on it?
- To verify real SUID behavior through hands-on testing
- To understand the difference between SGID and Sticky Bit in shared directories
- To analyze how sudo misconfiguration can lead to privilege escalation

---

## 3. What did I do?
### Hour 1
- Created a script as `root` containing system commands (`apt update`)
- Applied SUID to the script and executed it as `user1`
- Created files as `user1` and attempted modification as `user2`
- Applied Sticky Bit on a shared directory and tested file editing

### Hour 2
- Located the `sudo` binary
- Listed file permissions and ownership
- Reviewed sudo behavior under misconfigured `/etc/sudoers` rules

---

## 4. What did I observe?
### Hour 1
- SUID script execution failed with **Permission Denied**
- Sticky Bit on a shared directory blocked editor save operations due to rename behavior

### Hour 2
- Misconfigured sudoers rules can allow unauthorized users to run privileged commands
- `sudo` execution is logged by default unless logging is explicitly disabled or bypassed

---

## 5. What did I learn?
- SUID alone does not authorize execution of system-level commands like `apt`
- Command authorization is controlled by `/etc/sudoers`, not file permissions
- Sticky Bit should not be used on shared project directories
- Privilege escalation via sudo is caused by misconfiguration, not sudo binary flaws
- Sudo maintains audit logs by default, making misuse traceable

- ## 10-01-2026

### What I did
- Revised previous notes  
- Learned core concepts of programming languages (what & why)  
- Installed Python environment  
- Studied Python basics:
  - Modules  
  - pip  
  - Comments  

### Status
- Productive day ✅

- ### 📅 Daily Learning Log — 11-01-2026
**Time Spent:** 3 hours

## ✅ What I Learned Today

### 1. SUID Binaries
- Understood what SUID is and why it is needed  
- Verified SUID binaries run with file owner (root) privileges  
- Observed access to protected files during execution

### 2. sudo & sudoers
- Explored `/etc/sudoers` file  
- Learned sudo group members get full sudo privileges  
- Practical: created user → added to sudo group → tested sudo commands (worked)

### 3. Directory Permissions
- Understood rwx behavior on directories  
- Without `x` → cannot enter directory  
- Without `r` → cannot list contents  
- Tested behavior outside home directory

---

## 🔁 Revision of Previous Topics
- Revised:
  - chmod, chown, permissions  
  - SUID, SGID, Sticky Bit  
  - User/group concepts  

- Strengthened understanding of:
  - Privilege escalation basics  
  - Access control
---

## 🧠 Key Takeaway
> Wrong permissions or sudo config = serious security risk.

## 12-01-2026
**Time Spent:** 3 hours

### What I Practiced
- Listed SUID binaries using:
  - find / -perm -4000 -type f 2>/dev/null
- Analyzed behaviour of:
  - /usr/bin/sudo
  - /usr/bin/su
- Created a test user and configured sudo access
- Tested privilege escalation through sudo

---

### Binary Analysis

#### 1. /usr/bin/sudo

**Purpose:**  
Allows permitted users to execute commands as another user (usually root).

**Files Involved:**
- Authorization: /etc/sudoers  
- Authentication: /etc/pam.d/sudo → PAM reads /etc/shadow

**Why SUID Required:**  
Authentication requires access to /etc/shadow, which is readable only by root.

---

#### 2. /usr/bin/su

**Purpose:**  
Allows a user to switch to another account after successful authentication.

**Files Involved:**
- Authentication handled by PAM: /etc/pam.d/su  
- PAM accesses /etc/shadow for password verification

**Why SUID Required:**  
To allow non-root users to authenticate using protected password hashes.

---

### Security Observation

If sudoers contains:
user ALL=(ALL:ALL) ALL

Then the user can:
- Run any command as root
- Modify system files
- Edit /etc/shadow
- Fully compromise the system

This is a case of **privilege escalation due to sudoers misconfiguration**.

---

### Revision
- SUID, SGID, Sticky Bit behaviour
- Difference between authentication (PAM) and authorization (sudoers)


## Date: 18-01-2026

### What I Practiced
- SGID behavior on shared directories  
- Sticky bit behavior in world-writable directories  
- Real UID vs Effective UID using the `passwd` SUID binary  

---

## SGID (Set Group ID) on Directories

### Observation
- **Before SGID:**  
  Files created inside the shared directory inherited the creator’s **primary group** (e.g., user1, user2), which caused inconsistent permissions.

- **After SGID enabled:**  
  Files consistently inherited the directory group (`devteam`), allowing predictable collaboration.

### Example permission
- rwxrws---
The `s` in the group execute position confirms SGID is active.

### Key Insight
> SGID on directories enforces group ownership inheritance and prevents permission drift in shared environments like dev folders and web directories.

---

## Sticky Bit

### Before Sticky Bit
- user2 could delete files created by user1 in a world-writable directory.

### After Sticky Bit
- user2 could NOT delete or rename files owned by user1.

### Security Insight
> Sticky bit protects shared directories (like `/tmp`) by preventing users from deleting or renaming files they do not own, reducing the risk of sabotage and denial-of-service attacks.

---

## Privilege Logic (SUID, passwd, UID)

### Concepts
- **Real UID (RUID):** The user who launched the process  
- **Effective UID (EUID):** The privileges the process runs with (root for SUID binaries)

### passwd behavior
- `passwd` runs with **EUID = root** because it must modify `/etc/shadow`
- It still enforces authorization using the **Real UID**

### Authorization logic (simplified)
Allow if:
RUID == target user
OR RUID == 0 (root)
Else:
Deny


### Key Insight
> The passwd binary requires SUID because `/etc/shadow` is writable only by root. PAM handles authentication, but filesystem authorization is enforced by process privileges and internal program logic.

---

## Commands Used
- useradd, groupadd, usermod  
- chmod g+s, chmod +t  
- ls -l, ls -ld, id  
- passwd  

---

## Final Security Reflection
> SGID ensures stable collaboration permissions, sticky bit protects shared directories from abuse, and understanding RUID vs EUID is critical for understanding privilege boundaries and potential escalation paths.

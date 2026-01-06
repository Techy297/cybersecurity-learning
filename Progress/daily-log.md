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

## 01–05 Jan 2026
**Status:** Inconsistent / Partial execution  
**What I did:** College technical competition prep, light C revision, limited hands-on work  
**What went wrong:** No fixed routine, poor documentation, overthinking & distraction  
**Reality check:** Planning and imagination replaced execution  
**Lesson:** Consistency and logging matter more than intensity  
**Decision:** Reset discipline and resume daily task structure from 06-01-2026

### 🧠 One-line Reflection
Today I moved from “using Linux” to understanding how Linux decides.

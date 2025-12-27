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


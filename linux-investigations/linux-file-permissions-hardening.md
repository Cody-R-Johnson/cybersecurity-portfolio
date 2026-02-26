# Linux File Permission Hardening & Access Control Implementation

## Project Overview

This project documents a Linux-based access control review and remediation effort within the `/home/researcher2/projects` directory. The objective was to evaluate existing file and directory permissions, identify excessive access rights, and enforce least privilege principles using Linux command-line tools.

The task focused on correcting over-permissioned files, securing hidden files, and restricting directory execution rights to authorized users only.

---

## Environment

- Linux-based system
- Directory: `/home/researcher2/projects`
- Commands used:
  - `ls -la`
  - `chmod`

---

## Initial Assessment

Using:

```bash
ls -la
```

I generated a detailed listing of all files, including hidden files, within the projects directory.

### Directory Contents Identified

**Files:**
- project_k.txt
- project_m.txt
- project_r.txt
- project_t.txt
- .project_x.txt (hidden file)

**Subdirectory:**
- drafts

The 10-character permission strings revealed excessive access rights, particularly write permissions granted to "other" users.

---

## Understanding Linux Permission Structure

Each file displayed a 10-character permission string structured as:

```
[file type][user][group][other]
```

**Example:**
```
-rw-rw-r--
```

**Breakdown:**
- 1st character: file type (`-` = file, `d` = directory)
- Characters 2–4: user permissions
- Characters 5–7: group permissions
- Characters 8–10: other permissions

**Permission meanings:**
- `r` = read
- `w` = write
- `x` = execute
- `-` = permission not granted

This structure allowed identification of misconfigured access levels.

---

## Security Issues Identified

- Write permissions granted to "other" users on sensitive files.
- Hidden file `.project_x.txt` had improper group write access.
- Directory `drafts` allowed execute access to group users.
- Lack of strict least privilege enforcement.

These misconfigurations increased the risk of unauthorized modification and data tampering.

---

## Remediation Actions

### 1. Remove Write Access from "Other" Users

**File:** `project_k.txt`

```bash
chmod o-w project_k.txt
```

**Result:**
- Removed write access for "other"
- Verified changes using `ls -la`

---

### 2. Secure Hidden File (.project_x.txt)

**Organizational requirement:**
- No write access for anyone
- Read access allowed for user and group

**Commands used:**
```bash
chmod u-w,g-w,g+r .project_x.txt
```

**Actions performed:**
- Removed write permission from user
- Removed write permission from group
- Ensured group retained read permission

This prevented unauthorized modification of archived project data.

---

### 3. Restrict Directory Execution Rights

**Objective:**
Only researcher2 should have execute access to the drafts directory.

**Command used:**
```bash
chmod g-x drafts
```

**Outcome:**
- Removed execute permission from group
- Ensured only the owner retained directory traversal capability

This prevented unauthorized directory access and file enumeration.

---

## Security Principles Applied

- Least Privilege
- Access Control Enforcement
- Data Integrity Protection
- Secure File Management
- Principle of Need-to-Know

---

## Before vs After Risk Impact

| Issue | Risk Before | Risk After |
|-------|-------------|------------|
| Write access for other users | High | Removed |
| Hidden file write access | Medium | Removed |
| Excess directory execution | Medium | Restricted |
| Unstructured permissions | Elevated | Hardened |

---

## Skills Demonstrated

- Linux CLI proficiency
- File system permission analysis
- Access control hardening
- Permission string interpretation
- Risk reduction through configuration
- Use of `chmod` for granular permission control
- Security documentation

---

## Key Takeaways

Improper file permissions represent a common but critical security weakness in Linux systems. Excessive write or execute permissions can lead to:

- Unauthorized data modification
- Privilege abuse
- Accidental data corruption
- Insider threat exposure

Systematically reviewing permissions using `ls -la` and enforcing policy via `chmod` significantly reduces operational and security risk.

This project demonstrates foundational Linux security skills relevant to SOC analyst and security operations roles, particularly in environments where system configuration auditing and access control enforcement are required.

---

## Portfolio Note

This lab reflects applied Linux hardening techniques and reinforces the importance of least privilege in system administration and security operations.

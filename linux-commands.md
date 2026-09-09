# 👤 Linux User Management Guide

A production-ready, interactive command reference for creating, switching, and managing user accounts — with direct anchor navigation, quick-copy terminal code blocks, real-world examples, and open reference breakdowns.

---

## 📑 Table of Contents

### 👥 User Account Management
* [1. `adduser` — Create a New User Account](#1-adduser--create-a-new-user-account)
* [2. `su -` — Switch to Another User Account](#2-su----switch-to-another-user-account)
* [3. `exit` — Exit Current Shell / User Session](#3-exit--exit-current-shell--user-session)
* [4. `usermod -aG sudo` — Grant Root Privileges to a User](#4-usermod--ag-sudo--grant-root-privileges-to-a-user)
* [5. `deluser ... sudo` — Revoke Root Privileges from a User](#5-deluser--sudo--revoke-root-privileges-from-a-user)

---

## ⚡ Quick Command Matrix

| Command | Shorthand Syntax | Core Operation | Risk Level |
| :--- | :--- | :--- | :--- |
| **`adduser`** | `sudo adduser <name>` | Create new user account | Medium |
| **`su -`** | `su - <name>` | Switch to another user's shell | Low |
| **`exit`** | `exit` | Leave current user session | Low |
| **`usermod`** | `sudo usermod -aG sudo <name>` | Grant sudo (root) privileges | 🚨 High |
| **`deluser`** | `sudo deluser <name> sudo` | Revoke sudo (root) privileges | Medium |

---

## 👥 User Account Management

### 1. `adduser` — Create a New User Account
Creates a brand-new user account on the system. This is an interactive, higher-level wrapper around `useradd` that walks you through setting a password and optional account details.

```bash
sudo adduser "Account Name"
```

**Terminal Output Simulation:**
```text
[sudo] password for dhruv:
Adding user `newuser' ...
Adding new group `newuser' (1001) ...
Adding new user `newuser' (1001) with group `newuser' ...
Creating home directory `/home/newuser' ...
New password:
Retype new password:
passwd: password updated successfully
```

<details>
<summary>🔍 <b>How it works & breakdown</b></summary>

* **Step 1 — Root password:** Since `adduser` needs elevated rights, it first asks for **your** (the root/sudo) account password.
* **Step 2 — New account password:** After authentication, it prompts you to type and confirm a password for the **new** account being created.
* **Step 3 — Optional details:** You may be asked for full name, room number, phone, etc. — these can all be skipped by pressing `Enter`.
* **Result:** A new home directory (e.g. `/home/newuser`) is created automatically, along with a matching user group.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 2. `su -` — Switch to Another User Account
Switches your active shell session from the current (e.g. root) account into another user's account, loading that user's environment as if they had logged in directly.

```bash
su - NewAccountName
```

<details>
<summary>🔍 <b>Example Walkthrough</b></summary>

```bash
# Currently logged in as root
whoami
# root

# Switch into the new account
su - newuser
# Password: ********

# Confirm the switch
whoami
# newuser
```

* **Why the `-`?** The dash flag loads a full login shell — meaning the new user's home directory, environment variables, and shell profile (`.bashrc`, `.profile`) are applied correctly, exactly like a fresh login.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 3. `exit` — Exit Current Shell / User Session
Leaves the currently active user session and drops you back to the previous shell (e.g. back to `root` if you switched via `su -`).

```bash
exit
```

**Terminal Output Simulation:**
```text
newuser@machine:~$ exit
logout
root@machine:~#
```

> 💡 **Note:** This only pops you back one level. If you're several `su -` sessions deep, you'll need to run `exit` once for each level.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 4. `usermod -aG sudo` — Grant Root Privileges to a User
By default, a newly created user has **limited access** — they cannot run privileged commands. For example, running `sudo apt update` on a brand-new account will fail. This command adds the user to the `sudo` group, granting them full root-level powers.

```bash
sudo usermod -aG sudo AccountName
```

#### 🔍 Flag Breakdown (Always Visible)

| Flag | Name | Function |
| :--- | :--- | :--- |
| `-a` | Append | Adds the user to the group **without removing** them from existing groups |
| `-G` | Groups | Specifies the supplementary group(s) to modify — here, `sudo` |

<details>
<summary>🕹️ <b>Applying the Change</b></summary>

Group membership changes don't take effect on an already-open session. You must re-login to the account for the new privileges to load:

```bash
su - AccountName
```

Now the account has full root-equivalent powers, and commands like `sudo apt update` will succeed.
</details>

> 🚨 **Critical Safety Warning:** Only the `root` user has complete, unrestricted access to the machine. Granting `sudo` group membership effectively gives that account the same level of power — hand it out only to trusted accounts.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 5. `deluser ... sudo` — Revoke Root Privileges from a User
Removes a user from the `sudo` group, stripping their ability to run privileged/root-level commands while keeping the account itself intact.

```bash
sudo deluser newAccountname sudo
```

**Terminal Output Simulation:**
```text
Removing user `newAccountname' from group `sudo' ...
Done.
```

<details>
<summary>🔍 <b>How to verify</b></summary>

* **Check group membership:** Run `groups newAccountname` — `sudo` should no longer appear in the list.
* **Confirm restriction:** Log in as that user and try `sudo apt update`; it should now be denied.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

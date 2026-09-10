### 👤 User & Privilege Management
* [21. `adduser` — Create a New User Account](#21-adduser--create-a-new-user-account)
* [22. `su -` — Switch to User Account](#22-su---switch-to-user-account)
* [23. `exit` — Log Out of Current Session](#23-exit--log-out-of-current-session)
* [24. `usermod -aG sudo` — Grant Sudo (Admin) Privileges](#24-usermod--ag-sudo--grant-sudo-admin-privileges)
* [25. `deluser <user> sudo` — Revoke Sudo Privileges](#25-deluser-user-sudo--revoke-sudo-privileges)

---

## ⚡ User Privilege Matrix

| Command | Shorthand Syntax | Core Operation | Risk Level |
| :--- | :--- | :--- | :--- |
| **`adduser`** | `sudo adduser <name>` | Create new user profile with home directory | Medium |
| **`su -`** | `su - <name>` | Switch user with loaded environment | Low |
| **`exit`** | `exit` | Terminate session / return to caller shell | Low |
| **`usermod`** | `sudo usermod -aG sudo <name>` | Append user to sudo admin group | 🚨 High |
| **`deluser`** | `sudo deluser <name> sudo` | Revoke administrative root permissions | Medium |

---

## 👤 User & Privilege Management

### 21. `adduser` — Create a New User Account
Creates a complete user environment, including a home directory (`/home/<username>`), dedicated user group, and default shell configuration.

```bash
sudo adduser newuser
```

**Terminal Output Simulation:**
```text
Adding user `newuser' ...
Adding new group `newuser' (1001) ...
Adding new user `newuser' (1001) with group `newuser' ...
Creating home directory `/home/newuser' ...
New password:
Retype new password:
passwd: password updated successfully
```

[▲ Back to Table of Contents](#-table-of-contents)

---

### 22. `su -` — Switch to User Account
Switches your active shell session into another user's account, loading that user's full environment (home directory, shell profile, variables) as if they had logged in directly.

```bash
su - newuser
```

<details>
<summary>🔍 <b>Example Walkthrough</b></summary>

```bash
whoami
# root

su - newuser
# Password: ********

whoami
# newuser

pwd
# /home/newuser   ← correctly lands in newuser's home directory
```
</details>

<details>
<summary>🚨 <b>Common Mistake: forgetting the dash (`-`)</b></summary>

If you run `su newuser` **without** the dash, the user identity switches — but your current working directory and environment **stay exactly as they were** (they don't reload for the new user).

```bash
su shruti
# Password:

whoami
# shruti           ← user switched correctly

pwd
# /home/dhruv       ← BUT still in the old directory! Not /home/shruti
```

This confuses a lot of beginners because `whoami` says one thing while `pwd` says another. It's not a bug — `su` (no dash) only switches the user ID, it does **not** perform a full "fresh login." The dash (`-`) is what tells it to also reload the home directory and environment.

**Fix — always prefer the dash version:**
```bash
exit
su - shruti
pwd
# /home/shruti     ← correct now
```

| Command | User switches? | Directory changes to new user's home? | Environment reloads? |
| :--- | :--- | :--- | :--- |
| `su newuser` | ✅ Yes | ❌ No | ❌ No |
| `su - newuser` | ✅ Yes | ✅ Yes | ✅ Yes |
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 23. `exit` — Log Out of Current Session
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

> 💡 **Note:** This only pops you back one level. If you're several `su -` sessions deep (root → user1 → user2), you'll need to run `exit` once for each level to get all the way back to root.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 24. `usermod -aG sudo` — Grant Sudo (Admin) Privileges
By default, a newly created user has **limited access** — running `sudo` commands on a brand-new account will fail. This command adds the user to the `sudo` group, granting full root-level powers.

```bash
sudo usermod -aG sudo newuser
```

#### 🔍 Flag Breakdown (Always Visible)

| Flag | Name | Function |
| :--- | :--- | :--- |
| `-a` | Append | Adds the user to the group **without removing** them from existing groups |
| `-G` | Groups | Specifies the supplementary group(s) to modify — here, `sudo` |

<details>
<summary>🕹️ <b>Applying the Change</b></summary>

Group membership changes don't apply to an already-open session. You must re-login for the new privileges to take effect:

```bash
su - newuser
```

Now commands like `sudo apt update` will succeed for that account.
</details>

> 🚨 **Critical Safety Warning:** `sudo` group membership gives near root-level power. Only grant it to trusted accounts.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 25. `deluser <user> sudo` — Revoke Sudo Privileges
Removes a user from the `sudo` group, stripping their ability to run privileged commands, while keeping the account itself fully intact.

```bash
sudo deluser newuser sudo
```

**Terminal Output Simulation:**
```text
Removing user `newuser' from group `sudo' ...
Done.
```

<details>
<summary>🔍 <b>How to verify</b></summary>

* **Check group membership:** Run `groups newuser` — `sudo` should no longer appear in the list.
* **Confirm restriction:** Log in as that user and try `sudo apt update`; it should now be denied.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

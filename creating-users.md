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

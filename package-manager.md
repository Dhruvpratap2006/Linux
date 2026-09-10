# 📦 APT Package Manager Guide

A production-ready, interactive command reference for installing, updating, and removing software packages on Ubuntu/Debian — with direct anchor navigation, quick-copy terminal code blocks, real-world examples, and open reference breakdowns.

---

## 📑 Table of Contents

### 📥 Package Management
* [1. What is APT?](#1-what-is-apt)
* [2. `apt update` — Refresh Package List](#2-apt-update--refresh-package-list)
* [3. `apt upgrade` — Upgrade Installed Packages](#3-apt-upgrade--upgrade-installed-packages)
* [4. `apt install` — Install a New Package](#4-apt-install--install-a-new-package)
* [5. `apt remove` — Uninstall a Package](#5-apt-remove--uninstall-a-package)
* [6. `apt purge` — Completely Remove a Package](#6-apt-purge--completely-remove-a-package)
* [7. `apt show` — View Package Details](#7-apt-show--view-package-details)
* [8. `apt list --installed` — List Installed Packages](#8-apt-list---installed--list-installed-packages)

---

## ⚡ Quick Command Matrix

| Command | Shorthand Syntax | Core Operation | Risk Level |
| :--- | :--- | :--- | :--- |
| **`apt update`** | `sudo apt update` | Refresh the list of available packages | Low |
| **`apt upgrade`** | `sudo apt upgrade` | Upgrade all installed packages to latest version | Low |
| **`apt install`** | `sudo apt install <pkg>` | Install a new package | Medium |
| **`apt remove`** | `sudo apt remove <pkg>` | Uninstall a package, keep its config files | Medium |
| **`apt purge`** | `sudo apt purge <pkg>` | Uninstall a package + delete its config files | 🚨 High |
| **`apt show`** | `apt show <pkg>` | Show info/details about a package | Low |
| **`apt list --installed`** | `apt list --installed` | List all packages currently installed | Low |

---

## 📥 Package Management

### 1. What is APT?
APT (**Advanced Package Tool**) is Ubuntu/Debian's built-in package manager. Think of it like the Play Store or App Store, but for your Linux terminal — it lets you **install**, **update**, and **delete** software (called "packages") with a single command, instead of manually downloading files from the internet.

Every package (like `apache2` or `nginx`) is fetched from Ubuntu's official software repositories, so it's safe and pre-tested for your system.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 2. `apt update` — Refresh Package List
This does **not** install or upgrade anything. It just refreshes APT's local database with the latest list of available packages and their newest versions from Ubuntu's servers.

```bash
sudo apt update
```

**Terminal Output Simulation:**
```text
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Fetched 110 kB in 1s
Reading package lists... Done
```

<details>
<summary>🔍 <b>Why run this?</b></summary>

* Without running `update` first, APT may not know about the latest available versions of packages.
* **Best practice:** always run `sudo apt update` before installing or upgrading anything — it makes sure you get the newest, correct version.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 3. `apt upgrade` — Upgrade Installed Packages
Upgrades **all currently installed packages** on your system to their latest available versions (based on the list fetched by `apt update`).

```bash
sudo apt upgrade
```

<details>
<summary>🔍 <b>Example Walkthrough</b></summary>

```bash
# Step 1: Always refresh the list first
sudo apt update

# Step 2: Now upgrade everything that has a newer version
sudo apt upgrade
```

> 💡 **Note:** `apt update` and `apt upgrade` are two different things — `update` just refreshes the *list*, `upgrade` actually installs the newer versions. People often confuse them because the names sound similar.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 4. `apt install` — Install a New Package
Downloads and installs a new package (software) on your system.

```bash
sudo apt install apache2
```

```bash
sudo apt install nginx
```

<details>
<summary>🔍 <b>How it works & breakdown</b></summary>

* **`sudo`** → gives admin/root permission (required, since installing software affects the whole system).
* **`apt install`** → tells APT you want to install something.
* **`apache2` / `nginx`** → the exact package name you want installed.

**Common typo to avoid:** package names are case-sensitive and must be spelled exactly — `apche2` will fail, it must be `apache2`.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 5. `apt remove` — Uninstall a Package
Removes an installed package from your system, but **keeps its configuration files** behind (in case you reinstall it later and want your old settings back).

```bash
sudo apt remove apache2
```

```bash
sudo apt remove nginx
```

**Terminal Output Simulation:**
```text
Removing apache2 (2.4.52-1ubuntu4) ...
```

[▲ Back to Table of Contents](#-table-of-contents)

---

### 6. `apt purge` — Completely Remove a Package
Similar to `remove`, but goes a step further — it also **deletes the package's configuration files**. Use this when you want a completely clean uninstall, with zero leftovers.

```bash
sudo apt purge apache2
```

<details>
<summary>🕹️ <b>remove vs purge — what's the real difference?</b></summary>

| Action | Removes program? | Removes config files? |
| :--- | :--- | :--- |
| `apt remove` | ✅ Yes | ❌ No (kept for reinstall) |
| `apt purge` | ✅ Yes | ✅ Yes (fully wiped) |

> 🚨 **Safety Note:** Once you `purge` a package, any custom settings/config you had for it are gone for good. Use `remove` if you might reinstall it later.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 7. `apt show` — View Package Details
Displays detailed information about a package — like its version, size, description, and dependencies — **without installing it**. Useful to check what a package does before installing.

```bash
apt show nginx
```

**Terminal Output Simulation:**
```text
Package: nginx
Version: 1.18.0-6ubuntu14
Description: small, powerful, scalable web/proxy server
...
```

> 💡 **Note:** No `sudo` needed here — you're only *viewing* info, not changing anything on the system.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 8. `apt list --installed` — List Installed Packages
Shows a list of **every package currently installed** on your system.

```bash
apt list --installed
```

<details>
<summary>🔍 <b>Common mistake to watch out for</b></summary>

A frequent typo is writing `--install` (missing the "ed"):

```bash
apt list --install
# E: Command line option --install is not understood in combination with the other options
```

The correct flag is **`--installed`** (with "ed" at the end).

**Filtering a long list:** if you just want to check whether one specific package is installed, pipe it through `grep`:

```bash
apt list --installed | grep nginx
```
</details>

[▲ Back to Table of Contents](#-table-of-contents)
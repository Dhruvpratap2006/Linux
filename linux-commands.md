# 🐧 Complete Linux Terminal & Command-Line Guide

A production-ready, interactive command reference with direct anchor navigation, quick-copy terminal code blocks, real-world examples, and open reference breakdowns.

---

## 📑 Table of Contents

### 📍 Directory Navigation
* [1. `pwd` — Print Working Directory](#1-pwd--print-working-directory)
* [2. `ls` — List Directory Contents](#2-ls--list-directory-contents)
* [3. `clear` — Clear Terminal Viewport](#3-clear--clear-terminal-viewport)
* [4. `cd` — Change Directory](#4-cd--change-directory)
* [5. `cd ..` — Move One Level Up](#5-cd---move-one-level-up)
* [6. `cd ~` — Jump to User Home](#6-cd---jump-to-user-home)
* [7. `cd /` — Jump to Filesystem Root](#7-cd---jump-to-filesystem-root)

### 📂 Files & Directories Management
* [8. `mkdir` — Create New Directory](#8-mkdir--create-new-directory)
* [9. `mkdir -p` — Create Nested Directory Trees](#9-mkdir--p--create-nested-directory-trees)
* [10. `touch` — Create File or Update Timestamp](#10-touch--create-file-or-update-timestamp)
* [11. `cp` — Copy Files](#11-cp--copy-files)
* [12. `cp -r` — Copy Directories Recursively](#12-cp--r--copy-directories-recursively)
* [13. `mv` — Move or Rename Files & Folders](#13-mv--move-or-rename-files--folders)

### 🗑️ Removal & Cleanup
* [14. `rm` — Remove File](#14-rm--remove-file)
* [15. `rm -r` — Remove Directory Recursively](#15-rm--r--remove-directory-recursively)
* [16. `rm -rf` — Forcefully Remove Without Prompt](#16-rm--rf--forcefully-remove-without-prompt)
* [17. `rmdir` — Remove Empty Directory](#17-rmdir--remove-empty-directory)

### 📝 Editors & Inspection
* [18. `vim` — Modal Terminal Editor](#18-vim--modal-terminal-editor)
* [19. `nano` — Lightweight Terminal Editor](#19-nano--lightweight-terminal-editor)
* [20. `history` — Shell Execution Log](#20-history--shell-execution-log)

---

## ⚡ Quick Command Matrix

| Command | Shorthand Syntax | Core Operation | Risk Level |
| :--- | :--- | :--- | :--- |
| **`pwd`** | `pwd` | Print active directory path | Low |
| **`ls`** | `ls -lah` | List files, hidden items & sizes | Low |
| **`cd`** | `cd <path>` | Switch active directory | Low |
| **`mkdir`**| `mkdir -p a/b/c` | Make directory / recursive path | Low |
| **`touch`**| `touch <file>` | Create empty file / touch mtime | Low |
| **`cp`** | `cp -r src/ dst/` | Duplicate file or directory | Medium |
| **`mv`** | `mv old new` | Move or rename in-place | Medium |
| **`rm`** | `rm -rf <dir>` | Delete permanently | 🚨 High |
| **`vim`** | `vim <file>` | Modal console text editor | Low |
| **`nano`** | `nano <file>` | Interactive console text editor | Low |

---

## 📍 Directory Navigation

### 1. `pwd` — Print Working Directory
Displays the absolute path from the root directory (`/`) to your current working folder.

```bash
pwd
```

**Terminal Output Simulation:**
```text
/home/dhruv
```

<details>
<summary>🔍 <b>How to verify & breakdown</b></summary>

* **Meaning:** You are inside the `dhruv` personal folder under the system's `/home` tree.
* **Verification:** Run `echo $PWD` to confirm the environment variable matches.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 2. `ls` — List Directory Contents
Lists items inside the current directory. Supports flags to inspect hidden dotfiles, metadata, and storage consumption.

#### Basic List
```bash
ls
```

#### Detailed + Hidden + Human-Readable (Recommended)
```bash
ls -lah
```

**Terminal Output Simulation:**
```text
drwxr-xr-x  3 dhruv dhruv 4.0K Sep  9 18:30 .
drwxr-xr-x 18 dhruv dhruv 4.0K Sep  9 12:00 ..
-rw-r--r--  1 dhruv dhruv  220 Sep  9 14:12 .bashrc
drwxr-xr-x  2 dhruv dhruv 4.0K Sep  9 18:25 project1
-rw-r--r--  1 dhruv dhruv 1.2K Sep  9 18:30 notes.txt
```

#### 🔍 Flag Breakdown (Always Visible)

| Flag | Name | Function |
| :--- | :--- | :--- |
| `-l` | Long listing | Shows file permissions, link count, owner, group, size, and date |
| `-a` | All | Includes hidden dotfiles (e.g., `.bashrc`, `.env`, `.git`) |
| `-h` | Human-readable | Displays sizes in readable bytes (`4.0K`, `12M`, `2.1G`) |

[▲ Back to Table of Contents](#-table-of-contents)

---

### 3. `clear` — Clear Terminal Viewport
Clears all printed text from the visible screen buffer without terminating background processes or dropping history.

```bash
clear
```

> 💡 **Quick Shortcut:** Press `Ctrl` + `L` directly in your shell to achieve the exact same effect instantly.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 4. `cd` — Change Directory
Switches your shell's active working directory to the specified destination path.

```bash
cd project1
```

#### 🔍 Example Walkthrough (Always Visible)

```bash
# Verify initial location
pwd
# /home/dhruv

# Navigate into subdirectory
cd project1

# Verify updated location
pwd
# /home/dhruv/project1
```

[▲ Back to Table of Contents](#-table-of-contents)

---

### 5. `cd ..` — Move One Level Up
Moves up into the parent container directory (`..` represents parent directory).

```bash
cd ..
```

* **Starting point:** `/home/dhruv/project1`
* **Destination:** `/home/dhruv`

[▲ Back to Table of Contents](#-table-of-contents)

---

### 6. `cd ~` — Jump to User Home
Returns straight to your logged-in user's home directory from any path on the disk.

```bash
cd ~
```

*Equivalent shorthand:*
```bash
cd
```

[▲ Back to Table of Contents](#-table-of-contents)

---

### 7. `cd /` — Jump to Filesystem Root
Navigates straight to the very top root `/` of the Linux directory tree.

```bash
cd /
```

[▲ Back to Table of Contents](#-table-of-contents)

---

## 📂 Files & Directories Management

### 8. `mkdir` — Create New Directory
Creates an empty folder in your current active path.

```bash
mkdir test
```

[▲ Back to Table of Contents](#-table-of-contents)

---

### 9. `mkdir -p` — Create Nested Directory Trees
Generates nested parent and child directory trees in a single pass without failing if intermediate folders do not exist.

```bash
mkdir -p projects/backend/routes
```

**Resulting Directory Structure:**
```text
projects/
└── backend/
    └── routes/
```

[▲ Back to Table of Contents](#-table-of-contents)

---

### 10. `touch` — Create File or Update Timestamp
Generates a new empty file immediately. If the target file already exists, updates its `mtime` (last modified timestamp) without wiping content.

```bash
touch file.txt
```

[▲ Back to Table of Contents](#-table-of-contents)

---

### 11. `cp` — Copy Files
Creates an independent clone of a source file at the target path.

```bash
cp source.txt dest.txt
```

[▲ Back to Table of Contents](#-table-of-contents)

---

### 12. `cp -r` — Copy Directories Recursively
Duplicates a folder along with every single subfolder, nested directory, and file contained inside it.

```bash
cp -r source_dir dest_dir
```

[▲ Back to Table of Contents](#-table-of-contents)

---

### 13. `mv` — Move or Rename Files & Folders
Performs atomic moves across directories or renames items directly in the current location.

#### Move to a Directory
```bash
mv file.txt /home/dhruv/documents/
```

#### Rename in-place
```bash
mv old_name.txt new_name.txt
```

[▲ Back to Table of Contents](#-table-of-contents)

---

## 🗑️ Removal & Cleanup

### 14. `rm` — Remove File
Deletes a standard file permanently from disk.

```bash
rm file.txt
```

> ⚠️ **Warning:** Standard Linux shells do not have a GUI trash bin. Items removed via `rm` are permanently unlinked.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 15. `rm -r` — Remove Directory Recursively
Deletes a non-empty directory along with all nested contents.

```bash
rm -r old_project
```

[▲ Back to Table of Contents](#-table-of-contents)

---

### 16. `rm -rf` — Forcefully Remove Without Prompt
Combines recursive traversal (`-r`) with forced suppression of confirmation prompts (`-f`).

```bash
rm -rf temp_folder
```

> 🚨 **Critical Safety Warning:** Never execute `rm -rf` on root directories, wildcard paths (`rm -rf *`), or unverified shell variables.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 17. `rmdir` — Remove Empty Directory
Removes a directory strictly if it contains zero files and zero subfolders.

```bash
rmdir empty_folder
```

*If the directory contains even a single hidden file, it safely rejects deletion with an error.*

[▲ Back to Table of Contents](#-table-of-contents)

---

## 📝 Editors & Inspection

### 18. `vim` — Modal Terminal Editor
Opens the modal text editor in your terminal session.

```bash
vim file.txt
```

<details>
<summary>🕹️ <b>Interactive Vim Lifecycle & Cheat-Sheet</b></summary>

```text
[Normal Mode] ──(Press 'i')──> [Insert Mode: Type text]
     ▲                                   │
     │                                   │
     └──────────(Press 'Esc')────────────┘
```

1. **Enter Insert Mode:** Press `i` to begin writing text.
2. **Return to Normal Mode:** Press `Esc`.
3. **Save & Exit:** Type `:wq` and press `Enter`.
4. **Discard Changes & Exit:** Type `:q!` and press `Enter`.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 19. `nano` — Lightweight Terminal Editor
A modeless editor designed for immediate in-terminal edits with keybind hints shown on-screen.

```bash
nano file.txt
```

<details>
<summary>⌨️ <b>Nano Keybinds Reference</b></summary>

* **Save / Write Out:** `Ctrl` + `O` then press `Enter`
* **Exit:** `Ctrl` + `X`
* **Search / Find:** `Ctrl` + `W`
* **Cut Line:** `Ctrl` + `K`
* **Paste Line:** `Ctrl` + `U`
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 20. `history` — Shell Execution Log
Prints the chronological log of commands entered in the current and previous sessions.

```bash
history
```

**Terminal Output Simulation:**
```text
43  pwd
44  ls -lah
45  cd project1
46  touch app.js
47  history
```

> 💡 **Bonus Trick:** You can re-run any past command by typing `!` followed by its number (e.g., `!45` runs `cd project1`).

[▲ Back to Table of Contents](#-table-of-contents)

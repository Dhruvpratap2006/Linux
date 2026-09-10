# 💻 Linux Terminal Basics Guide

A simple, easy-to-read command reference for navigating, creating, and managing files and folders in the Linux terminal — with direct copy-pasteable code blocks and clear examples.

---

## 📑 Table of Contents

### 📍 Navigation
* [1. `pwd` — Show Current Directory](#1-pwd--show-current-directory)
* [2. `ls` — List Files and Folders](#2-ls--list-files-and-folders)
* [3. `clear` — Clear Terminal Screen](#3-clear--clear-terminal-screen)
* [4. `cd` — Change Directory](#4-cd--change-directory)
* [5. `cd ..` — Go One Level Up](#5-cd----go-one-level-up)
* [6. `cd ~` — Go to Home Directory](#6-cd----go-to-home-directory)
* [7. `cd /` — Go to Root Directory](#7-cd----go-to-root-directory)

### 📂 Creating Files & Folders
* [8. `mkdir` — Create a New Folder](#8-mkdir--create-a-new-folder)
* [9. `mkdir -p` — Create Nested Folders](#9-mkdir--p--create-nested-folders)
* [10. `touch` — Create a New File](#10-touch--create-a-new-file)

### 🗑️ Deleting Files & Folders
* [11. `rm` — Remove a File](#11-rm--remove-a-file)
* [12. `rm -r` — Remove a Folder + Contents](#12-rm--r--remove-a-folder--contents)
* [13. `rm -rf` — Force Remove](#13-rm--rf--force-remove)
* [14. `rmdir` — Remove an Empty Folder](#14-rmdir--remove-an-empty-folder)

### 📋 Copying & Moving
* [15. `cp` — Copy a File](#15-cp--copy-a-file)
* [16. `cp -r` — Copy a Folder](#16-cp--r--copy-a-folder)
* [17. `mv` — Move or Rename](#17-mv--move-or-rename)

### 📝 Terminal Editors
* [18. `vim` — Edit Files in Vim](#18-vim--edit-files-in-vim)
* [19. `nano` — Edit Files in Nano](#19-nano--edit-files-in-nano)

### 📜 History
* [20. `history` — Show Previous Commands](#20-history--show-previous-commands)

---

## ⚡ Quick Command Matrix

| Command | Shorthand Syntax | Core Operation | Risk Level |
| :--- | :--- | :--- | :--- |
| **`pwd`** | `pwd` | Show current folder path | Low |
| **`ls`** | `ls` / `ls -lah` | List files and folders | Low |
| **`clear`** | `clear` | Clear the terminal screen | Low |
| **`cd`** | `cd <folder>` | Move into a folder | Low |
| **`mkdir`** | `mkdir <name>` | Create a new folder | Low |
| **`touch`** | `touch <file>` | Create a new empty file | Low |
| **`rm`** | `rm <file>` | Delete a file permanently | Medium |
| **`rm -rf`** | `rm -rf <folder>` | Force-delete folder + contents | 🚨 High |
| **`rmdir`** | `rmdir <folder>` | Delete an empty folder | Low |
| **`cp`** | `cp <src> <dest>` | Copy a file or folder | Low |
| **`mv`** | `mv <src> <dest>` | Move or rename a file/folder | Medium |
| **`vim` / `nano`** | `vim <file>` / `nano <file>` | Edit a file in the terminal | Low |
| **`history`** | `history` | Show previously run commands | Low |

---

## 📍 Navigation

### 1. `pwd` — Show Current Directory
Tells you exactly which folder you're standing in right now, using the full path.

```bash
pwd
```

**Example Output:**
```text
/home/dhruv
```

<details>
<summary>🔍 <b>Simple example</b></summary>

Think of your terminal like walking through a building with many rooms (folders). `pwd` just tells you: "You are currently in this exact room" — so you never lose track of where you are.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 2. `ls` — List Files and Folders
Shows everything (files and folders) sitting inside your current directory.

```bash
ls
```

**Example Output:**
```text
project1  notes.txt
```

<details>
<summary>🔍 <b>Useful variations</b></summary>

**`ls -l` — Detailed list**
Shows permissions, owner, size, and last modified date/time for each item.
```bash
ls -l
```

**`ls -a` — Show hidden files**
Linux hides certain files by default (their names start with a dot `.`, like `.bashrc`). This flag reveals them too.
```bash
ls -a
```
```text
.bashrc  .profile  notes.txt
```

**`ls -lah` — All three combined**
This is the most commonly used combo:
- `-l` → detailed info
- `-a` → hidden files too
- `-h` → sizes shown in easy-to-read KB/MB/GB instead of raw bytes
```bash
ls -lah
```
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 3. `clear` — Clear Terminal Screen
Wipes everything currently visible on your terminal screen, giving you a clean, empty view.

```bash
clear
```

**Keyboard shortcut:** `Ctrl + L` does the same thing.

> 💡 **Note:** This only clears what's *shown on screen* — it does **not** delete your command history. Your old commands are still saved and can be recalled with `history`.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 4. `cd` — Change Directory
Moves you from your current folder into another one.

```bash
cd project1
```

<details>
<summary>🔍 <b>Simple example</b></summary>

If you're in `/home/dhruv` and run `cd project1`, you move into `/home/dhruv/project1`. It's exactly like opening a folder by double-clicking it — except in the terminal, you type its name instead.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 5. `cd ..` — Go One Level Up
Moves you back up to the **parent folder** — one step outward from where you are.

```bash
cd ..
```

<details>
<summary>🔍 <b>Simple example</b></summary>

If you're currently at:
```text
/home/dhruv/project1
```
running `cd ..` takes you to:
```text
/home/dhruv
```

**Remember it like this:** `..` always means "the folder one step above me."
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 6. `cd ~` — Go to Home Directory
Instantly jumps you back to your personal home folder, no matter how deep you are.

```bash
cd ~
```

You can also just type `cd` alone (with nothing after it) — both do the same thing.

```bash
cd
```

Both take you straight to something like `/home/dhruv`.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 7. `cd /` — Go to Root Directory
Takes you to `/` — the very top-most folder of the entire Linux filesystem. Every other folder (including your home folder) lives somewhere inside this one.

```bash
cd /
```

> 💡 **Note:** Think of `/` as the "ground floor" of your whole computer — everything else branches out from here.

[▲ Back to Table of Contents](#-table-of-contents)

---

## 📂 Creating Files & Folders

### 8. `mkdir` — Create a New Folder
Creates a brand-new, empty folder.

```bash
mkdir test
```

This creates a folder named `test/` right where you are.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 9. `mkdir -p` — Create Nested Folders
Creates a whole chain of folders inside one another, in a single command — even if the in-between folders don't exist yet.

```bash
mkdir -p projects/backend/routes
```

**Result:**
```text
projects/
└── backend/
    └── routes/
```

<details>
<summary>🔍 <b>Simple example</b></summary>

Without `-p`, trying to create `projects/backend/routes` directly would fail if `projects` and `backend` don't already exist. The `-p` flag (short for "parents") automatically creates every missing folder along the way.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 10. `touch` — Create a New File
Creates a new, completely empty file.

```bash
touch file.txt
```

> 💡 **Note:** If `file.txt` already exists, `touch` doesn't erase it — it just updates the file's "last modified" timestamp, leaving the content untouched.

[▲ Back to Table of Contents](#-table-of-contents)

---

## 🗑️ Deleting Files & Folders

### 11. `rm` — Remove a File
Permanently deletes a single file.

```bash
rm file.txt
```

> ⚠️ **Warning:** Linux does not have a recycle bin by default — once deleted with `rm`, the file is gone for good.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 12. `rm -r` — Remove a Folder + Contents
Deletes an entire folder, along with everything inside it.

```bash
rm -r old_project
```

`-r` stands for **recursive** — it means "go through this folder and everything inside it, one by one."

[▲ Back to Table of Contents](#-table-of-contents)

---

### 13. `rm -rf` — Force Remove
Forcefully deletes a folder and all its contents — without asking "are you sure?" first.

```bash
rm -rf temp_folder
```

* `-r` → recursive (go through everything inside)
* `-f` → force (skip confirmation prompts)

> 🚨 **Critical Warning:** This is one of the most dangerous commands in Linux. There is **no undo**. Always double-check the folder name before running it — never run this carelessly, especially with `/` or a variable that might be empty.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 14. `rmdir` — Remove an Empty Folder
Deletes a folder, but **only if it's completely empty**.

```bash
rmdir empty_folder
```

> 💡 **Note:** If the folder has anything inside it, this command will give an error. Use `rm -r` instead if you want to delete a folder that has files in it.

[▲ Back to Table of Contents](#-table-of-contents)

---

## 📋 Copying & Moving

### 15. `cp` — Copy a File
Makes a duplicate copy of a file.

```bash
cp source.txt dest.txt
```

This creates a new file `dest.txt` with the same content as `source.txt` — the original file stays exactly where it was.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 16. `cp -r` — Copy a Folder
Copies an entire folder, along with everything inside it.

```bash
cp -r source_dir dest_dir
```

`-r` (recursive) is required here — without it, `cp` won't know how to copy a folder's contents.

[▲ Back to Table of Contents](#-table-of-contents)

---

### 17. `mv` — Move or Rename
Does two jobs depending on how you use it: **moving** a file to a new location, or **renaming** it.

**Move a file to another folder:**
```bash
mv file.txt /home/dhruv/documents/
```

**Rename a file:**
```bash
mv old_name.txt new_name.txt
```

<details>
<summary>🔍 <b>Simple way to remember</b></summary>

`mv` = **m**o**v**e OR **r**e**n**a**m**e — Linux treats renaming as just "moving" a file to a new name in the same place. There's no separate "rename" command.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

## 📝 Terminal Editors

### 18. `vim` — Edit Files in Vim
Opens a powerful (but slightly tricky for beginners) text editor directly inside the terminal.

```bash
vim file.txt
```

If `file.txt` doesn't exist yet, Vim will create it once you save.

<details>
<summary>🔍 <b>Quick Vim workflow</b></summary>

1. Open the file: `vim file.txt`
2. Press **`i`** to enter Insert Mode (now you can actually type)
3. Type your content
4. Press **`Esc`** to leave Insert Mode
5. Type **`:wq`** and press `Enter` to save and quit

**To quit without saving:** Press `Esc`, then type `:q!` and press `Enter`.
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

### 19. `nano` — Edit Files in Nano
Opens a much simpler, beginner-friendly text editor in the terminal.

```bash
nano file.txt
```

You can start typing immediately — no special "insert mode" needed like Vim.

<details>
<summary>🔍 <b>Quick Nano shortcuts</b></summary>

* **Save:** `Ctrl + O`, then press `Enter`
* **Exit:** `Ctrl + X`
</details>

[▲ Back to Table of Contents](#-table-of-contents)

---

## 📜 History

### 20. `history` — Show Previous Commands
Shows a numbered list of every command you've run recently in this terminal.

```bash
history
```

**Example Output:**
```text
43  pwd
44  ls
45  cd project1
46  ls -lah
```

> 💡 **Note:** Handy when you forget the exact command you typed earlier — just scroll up through your history instead of retyping it.

[▲ Back to Table of Contents](#-table-of-contents)

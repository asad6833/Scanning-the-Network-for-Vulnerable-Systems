# Kali Linux Network Configuration & Interface Analysis Lab

---

## 1. Lab Environment — Kali Linux VM Overview

- The VM is running the **Kali Linux penetration testing / forensics distribution** created and maintained by Offensive Security (kali.org).
- Kali is based on the **Debian** Linux distribution and uses the **GNOME** desktop environment.
- The lab is accessed as a **virtual machine (VM)**.

### 1.1 Input Limitations

- The virtual hosting of Kali Linux **does not support TypeText**.
- All commands must be **typed manually** in the terminal.
- Commands are case-sensitive and should be entered exactly as shown.

---

## 2. Logging In and Desktop Basics

1. Select the **KALI** VM.
2. Sign in as the **root** user:
   - Username: `root`
   - Password: `Pa$$w0rd`
3. If the desktop is hidden or locked:
   - Drag the privacy shader **up** if it is lowered, **or**
   - If the screen is black, go to **Display → Reconnect**.

### 2.1 Desktop Shortcuts

The desktop includes shortcuts to:

- **Trash**
- **File System** (root `/`)
- **Home** (the logged-on user’s home folder, such as `/root`)

### 2.2 Top Panel Overview

- Left side: shortcuts to:
  - Show desktop / minimize all windows
  - File browser
  - Text editor
  - Firefox web browser
  - Terminal emulator
- Center: **virtual workspaces** (1, 2, 3, 4) for organizing windows.
- Right side: system icons:
  - Network
  - Volume
  - Notifications
  - Power (computer)
  - Clock
  - Lock Screen
  - Log Out / Shutdown

---

## 3. Working with the Terminal

### 3.1 Opening a Terminal

- Right-click on the desktop and select **Open Terminal Here**.
- Because you opened it from the desktop, the initial working directory is:
  ```bash
  /root/Desktop
  ```
- You can verify this with:
  ```bash
  pwd
  ```

### 3.2 Prompt and Home Directory

- The prompt uses `~` to represent the current user's home directory (`/root` for the root user).
- When instructions say **enter**, it means:
  - Type the command.
  - Press **ENTER**.

---

## 4. Network Configuration (eth0)

### 4.1 View Interface Configuration

Use the following command to inspect the configuration of `eth0`:

```bash
ip a s eth0
```

- The output shows MAC address, IPv4, and IPv6 configuration.
- In this lab environment, the VM is configured via **DHCP reservations**.
- `eth0` should always receive an address whose host part ends in `.66`.  
  Example:
  ```text
  10.1.16.66
  ```

> ⚠️ The KALI machine has a **second adapter (`eth1`)** used for graded activities.  
> Do **not** modify any settings for `eth1`.

### 4.2 Screenshot — `ip a s eth0` Output

Below is a screenshot of the `ip a s eth0` command output in the Kali terminal:

![Kali eth0 configuration output](Screenshot 2025-11-28 at 4.28.06 PM.png)

---

## 5. Lab Activities & Question Types

During the lab you will see three kinds of scored items:

### 5.1 Inline Questions

- Check that you understand a concept or step that was just demonstrated.
- If your answer is incorrect, you can retry until you select the correct option.

**Example — Inline Question**

1. In the terminal, run:
   ```bash
   hostname
   ```
2. Question: **What is the name of the Kali VM?**

   - kali  
   - PC10  
   - Linux10  
   - VM-Kali  
   - root  

   Correct answer (from the command output): **`kali`**

---

### 5.2 Verification Tasks

- These confirm that you ran a command **exactly as specified**.
- Commands, filenames, and letter case must match the instructions.
- Example: if asked to create `user01`, answers such as `user1` or `User01` are **incorrect**.

**Example — Verification Step**

Run:

```bash
ip a | grep eth0 > eth0_Config.txt
```

- This command filters `ip a` output for `eth0` and redirects it to a file named **`eth0_Config.txt`**.
- The file should appear on the **Desktop**.
- Clicking the **Score** button runs a script to verify that:
  - The file exists.
  - The command was executed correctly.

Then view the contents:

```bash
cat eth0_Config.txt
```

You may then be asked, for example:

> “Please enter the `inet` (IPv4) address for `eth0` shown in `eth0_Config.txt`.  
> Do **not** include the slash or any numbers after it.”

You would type the IPv4 address only (for example):

```text
10.1.16.66
```

### 5.3 Screenshot — `eth0_Config.txt` Contents

Below is a screenshot showing the creation and display of `eth0_Config.txt`:

![Kali eth0_Config.txt contents](Screenshot 2025-11-28 at 4.37.37 PM.png)

---

### 5.4 Comprehensive Questions

- These appear at the **end of the lab**.
- They test overall understanding of tools and tasks used throughout the lab.
- Questions may be:
  - Single correct answer (radio buttons), or
  - Multiple correct answer (checkboxes).
- You can use the **Previous** button in the lab interface to review earlier instructions before answering.
- If you get a question wrong, you can retry until you select the correct answer.

---

## 6. Closing the Terminal

When finished with the terminal in this phase of the lab:

- Click the **X** button in the top-right corner of the terminal window to close it.

---

## 7. Notes for GitHub Repository

When you move this file into a GitHub repository, you might use a structure like:

```text
kali-network-lab/
├─ screenshots/
│  ├─ Screenshot 2025-11-28 at 4.28.06 PM.png
│  └─ Screenshot 2025-11-28 at 4.37.37 PM.png
└─ README.md
```

- Place the two PNG files into a `screenshots/` folder.
- Adjust the image links above to:
  ```markdown
  ![Kali eth0 configuration output](screenshots/Screenshot 2025-11-28 at 4.28.06 PM.png)
  ![Kali eth0_Config.txt contents](screenshots/Screenshot 2025-11-28 at 4.37.37 PM.png)
  ```

# procfind

`procfind` is a lightweight ```bash utility for quickly finding, monitoring, and managing processes on Linux.  
It’s designed for speed, clarity, and convenience, with color highlighting and optional interactive kill mode.  

---

## ✨ Features

- **Process Search**
  - Quickly locate processes by name (case-insensitive)
  - Highlights matches in red for easy scanning
  - Displays PID, CPU usage, memory usage, command, and arguments

- **Follow Mode (`-f`)**
  - Continuously updates the process list in real time
  - Useful for monitoring CPU/memory usage live
  - Clears and redraws every 2 seconds

- **Kill Mode (`-k` / `--kill`)**
  - Lists matching processes in a numbered table (with headings)
  - Lets you select:
    - A specific process by number
    - `(A)` to kill all matches at once
  - Uses standard `kill` command to terminate

- **Self-Update Check**
  - If the script is inside a cloned Git repository, it automatically checks for updates on launch
  - Prompts to update if a newer version is available
  - Runs `git pull` to fetch and sync changes in place

- **Installable Symlink**
  - Automatically detects if it’s installed at `/usr/bin/procfind`
  - Prompts to create/update symlink for global access

---

## 📦 Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/procfind.git
cd procfind
```

2. Make the Script Executable

```bash

chmod +x procfind.sh
```
3. (Optional) Install Globally
Run the script once — if not installed, it will prompt to create a symlink:

```bash

./procfind.sh
```
Confirm with y to install as /usr/bin/procfind.

## 🚀 Usage
Basic Search
```bash

procfind firefox
```
Finds all running processes with "firefox" in the name or arguments.

Follow Mode
```bash

procfind -f firefox
```
Updates the list every 2 seconds to monitor usage in real time.

Kill Mode
```bash

procfind -k firefox
```
Example output:

```pgsql

Processes matching "firefox":
#    PID      %CPU   %MEM   COMMAND             ARGS
1    1234     12.5   1.2    firefox             firefox
2    2345     0.0    0.8    firefox             firefox --new-tab example.com

Enter process number to kill (or 'A' to kill all): 
```

Combined Options
You can combine flags:

```bash

procfind -f -k firefox
```
(Follow mode + kill prompt — kills once, then resumes monitoring.)

## 🔄 Updating
If installed from git clone, procfind will:

Check for updates when run

Prompt to git pull if changes are detected

Exit after update so you can restart with the latest version

You can also update manually:

```bash

cd /path/to/procfind
git pull
```
## 📜 License
MIT License – feel free to use, modify, and distribute.

## 🛠 Requirements
Linux system with bash, awk, sed, and ps

Git (for update feature if cloned from a repo)
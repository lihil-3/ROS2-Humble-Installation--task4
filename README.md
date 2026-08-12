# 🤖 ROS 2 Humble Installation on Ubuntu 22.04

## 📌 Task 4 – Linux and ROS Installation

## 📖 Overview

This task focused on installing a Linux environment and setting up ROS 2 Humble.

Ubuntu 22.04.5 LTS was installed using Windows Subsystem for Linux 2 (WSL 2), followed by the installation, configuration, and testing of ROS 2 Humble.

---

## 🐧 1. Linux Environment Installation

The Linux environment was installed using Windows Subsystem for Linux (WSL 2).

The required Windows features were enabled using PowerShell as Administrator:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

After restarting the computer, WSL was updated:

```powershell
wsl --update
```

WSL 2 was then configured as the default version:

```powershell
wsl --set-default-version 2
```

---

## 🐧 2. Installing Ubuntu 22.04

Ubuntu 22.04 LTS was selected because it is compatible with ROS 2 Humble.

The available Linux distributions were checked using:

```powershell
wsl --list --online
```

Ubuntu 22.04 was then installed:

```powershell
wsl --install Ubuntu-22.04
```

After installation, a Linux username and password were created.

The Ubuntu version was verified using:

```bash
lsb_release -a
```

**✅ Installed Version**

```
Ubuntu 22.04.5 LTS (Jammy Jellyfish)
```

📸 *Screenshot*

---

## 🔄 3. Updating Ubuntu

Before installing ROS 2, the Ubuntu package lists were updated:

```bash
sudo apt update
```

The installed packages were then upgraded:

```bash
sudo apt upgrade -y
```

Both commands completed successfully.

---

## 📦 4. Setting Up the ROS 2 Repository

The ROS 2 repository was configured before installing ROS 2 Humble.

The ROS key was downloaded using:

```bash
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

The ROS 2 repository was then added:

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

After adding the repository, the package list was updated:

```bash
sudo apt update
```

---

## 🤖 5. Installing ROS 2 Humble

ROS 2 Humble Desktop was installed using:

```bash
sudo apt install ros-humble-desktop
```

The installation completed successfully.

📸 *Screenshot*

---

## ⚙️ 6. Configuring the ROS Environment

The ROS 2 environment was activated using:

```bash
source /opt/ros/humble/setup.bash
```

To automatically load ROS 2 whenever Ubuntu starts, the following command was added to `.bashrc`:

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```

The configuration was then reloaded:

```bash
source ~/.bashrc
```

---

## 🧪 7. Testing ROS 2

The ROS 2 installation was tested using the ROS diagnostic tool:

```bash
ros2 doctor
```

**✅ Result**

```
All 5 checks passed.
```

This confirmed that the ROS 2 environment was correctly installed and configured.

📸 *Screenshot*

---

## 💬 8. Running a ROS 2 Node

To verify that ROS 2 could successfully run a node, the following command was executed:

```bash
ros2 run demo_nodes_cpp talker
```

The terminal successfully displayed messages such as:

```
Hello World: 1
Hello World: 2
Hello World: 3
Hello World: 4
```

The continuous messages confirmed that the ROS 2 Talker node was running successfully.

The node was stopped using:

```
Ctrl + C
```

📸 *Screenshot*

---

## ⚠️ 9. Problems Encountered and Solutions

### 🔴 Problem 1 – WSL Command Not Recognized

At the beginning, the following command was not recognized by PowerShell:

```powershell
wsl --install
```

**💡 Solution**

The required Windows features were enabled manually using DISM commands for Windows Subsystem for Linux and Virtual Machine Platform.

After restarting the computer, WSL was successfully configured.

---

### 🟠 Problem 2 – WSL Required an Update

When configuring WSL 2, the system indicated that WSL required an update.

**💡 Solution**

WSL was updated using:

```powershell
wsl --update
```

After the update, WSL 2 was successfully configured using:

```powershell
wsl --set-default-version 2
```

---

### 🟡 Problem 3 – `lsb_release` Command Typing Error

The Ubuntu version command was initially entered incorrectly.

❌ **Incorrect Command**

```bash
lsb_release-a
```

✅ **Correct Command**

```bash
lsb_release -a
```

The correct command successfully displayed Ubuntu 22.04.5 LTS.

---

### 🟢 Problem 4 – `ros2 --version` Command

The following command did not provide the expected version information:

```bash
ros2 --version
```

**💡 Solution**

The ROS installation was verified using the ROS diagnostic tool instead:

```bash
ros2 doctor
```

The result was:

```
All 5 checks passed.
```

The Talker node was also successfully executed:

```bash
ros2 run demo_nodes_cpp talker
```

The node successfully published continuous Hello World messages, confirming that ROS 2 was working correctly.

---

## 📸 10. Screenshots

**Ubuntu 22.04 Version**
Ubuntu 22.04.5 LTS was successfully installed and verified.

**ROS 2 Humble Installation**
ROS 2 Humble Desktop was successfully installed.

**ROS 2 Doctor**
All five ROS diagnostic checks passed successfully.

**ROS 2 Talker**
The ROS 2 Talker node successfully published Hello World messages.

---

## ✅ 11. Final Result

| Component | Status |
|---|---|
| WSL | ✅ Installed |
| WSL 2 | ✅ Configured |
| Ubuntu 22.04.5 LTS | ✅ Installed |
| ROS 2 Humble | ✅ Installed |
| ROS Environment | ✅ Configured |
| ROS Doctor | ✅ 5/5 Checks Passed |
| ROS 2 Talker Node | ✅ Running Successfully |

---

## 🎯 Conclusion

Ubuntu 22.04.5 LTS was successfully installed using WSL 2, and ROS 2 Humble was successfully installed and configured.

The installation was verified using `ros2 doctor`, which reported **All 5 checks passed**.

The ROS 2 Talker node was also successfully executed and published continuous Hello World messages.

Therefore, the Linux and ROS 2 environment was successfully installed, configured, and tested.

---

## Author

Hind Almutairi

Computer Science Student


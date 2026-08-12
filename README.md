ROS 2 Humble Installation on Ubuntu 22.04

Task 4 – Linux and ROS Installation

Overview

This task focused on installing a Linux environment and setting up ROS 2 Humble. Ubuntu 22.04 LTS was installed using Windows Subsystem for Linux 2 (WSL 2), followed by the installation and testing of ROS 2 Humble.

⸻

1. Linux Environment Installation

The Linux environment was installed using Windows Subsystem for Linux (WSL 2).

First, the required Windows features were enabled using PowerShell:

dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

After restarting the computer, WSL was updated and configured to use version 2:

wsl --update
wsl --set-default-version 2

⸻

2. Installing Ubuntu 22.04

Ubuntu 22.04 LTS was selected because it is compatible with ROS 2 Humble.

The available Linux distributions were checked using:

wsl --list --online

Ubuntu 22.04 was then installed:

wsl --install Ubuntu-22.04

After installation, a Linux username and password were created.

The Ubuntu version was verified using:

lsb_release -a

The installed version was:

Ubuntu 22.04.5 LTS (Jammy Jellyfish)

⸻

3. Updating Ubuntu

Before installing ROS 2, the Ubuntu packages were updated:

sudo apt update

Then the installed packages were upgraded:

sudo apt upgrade -y

Both commands completed successfully.

⸻

4. Setting Up the ROS 2 Repository

The ROS 2 repository and required tools were configured.

The ROS key was downloaded using:

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

The ROS 2 repository was then added:

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

After adding the repository, the package list was updated:

sudo apt update

⸻

5. Installing ROS 2 Humble

ROS 2 Humble Desktop was installed using:

sudo apt install ros-humble-desktop

The installation completed successfully.

⸻

6. Configuring the ROS Environment

The ROS environment was activated using:

source /opt/ros/humble/setup.bash

To automatically load ROS whenever Ubuntu starts, the following command was added to .bashrc:

echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc

Then the configuration was reloaded:

source ~/.bashrc

⸻

7. Testing ROS 2

The ROS installation was tested using:

ros2 doctor

The diagnostic test successfully passed all checks:

All 5 checks passed.

This confirmed that the ROS 2 environment was correctly installed and configured.

⸻

8. Running a ROS 2 Node

To verify that ROS 2 could run a node successfully, the following command was executed:

ros2 run demo_nodes_cpp talker

The terminal successfully displayed messages such as:

Hello World: 1
Hello World: 2
Hello World: 3
Hello World: 4

This confirmed that the ROS 2 Talker node was running successfully.

The node was stopped using:

Ctrl + C

⸻

9. Problems Encountered and Solutions

Problem 1 – WSL Command Not Recognized

At the beginning, the command:

wsl --install

was not recognized by PowerShell.

Solution:
The required Windows features were enabled manually using DISM commands for WSL and Virtual Machine Platform.

⸻

Problem 2 – WSL Required an Update

When configuring WSL 2, the system indicated that WSL required an update.

Solution:

wsl --update

After updating WSL, version 2 was successfully configured.

⸻

Problem 3 – lsb_release Command Typing Error

Initially, the Ubuntu version command was entered incorrectly.

The incorrect command was:

lsb_release-a

The correct command was:

lsb_release -a

The correct command successfully displayed Ubuntu 22.04.5 LTS.

⸻

Problem 4 – ros2 --version Command

The command:

ros2 --version

did not provide the expected version information.

Solution:
The ROS installation was verified using the ROS diagnostic tool instead:

ros2 doctor

The result showed:

All 5 checks passed.

The Talker node was also successfully executed, providing an additional confirmation that ROS 2 was working correctly.

⸻

10. Screenshots

Ubuntu 22.04 Version

The Ubuntu installation was verified using lsb_release -a.

ROS 2 Installation

ROS 2 Humble Desktop was successfully installed.

ROS 2 Doctor

All ROS diagnostic checks passed successfully.

ROS 2 Talker

The ROS 2 Talker node successfully published Hello World messages.

⸻

11. Conclusion

Ubuntu 22.04 LTS was successfully installed using WSL 2, and ROS 2 Humble was successfully installed and configured.

The installation was verified using ros2 doctor, which passed all five checks. The ROS 2 Talker node was also successfully executed and published Hello World messages.

Therefore, the Linux and ROS 2 environment was successfully installed and tested.

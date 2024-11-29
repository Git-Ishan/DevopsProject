# Script to install Jenkins

![Screenshot from 2024-11-29 12-15-15](https://github.com/user-attachments/assets/c0016c10-78a2-4840-ad10-6513d6d2d659)

This Bash script automates the installation of Java 17 and Jenkins on Ubuntu, Red Hat, or macOS platforms. The `identify_platform` function detects the OS type using `OSTYPE` and available package managers (`apt`, `yum`, or `brew`). Based on the detected platform, `setup_java` installs OpenJDK 17, and `setup_jenkins` installs Jenkins using the appropriate package manager and keys. Both functions handle platform-specific commands to ensure compatibility. The script exits if an unsupported platform is detected. The `execute_tasks` function orchestrates the process, running platform detection first and then sequentially setting up Java and Jenkins. Finally, it provides guidance to access Jenkins via a browser.


# Setup Master-slave architecture
Setting up a node for a master-slave architecture by utilizing the private key, username, and host details from a remote system, and it is capable of executing 5 tasks at a time
![Screenshot from 2024-11-29 12-23-01](https://github.com/user-attachments/assets/b7d2aad5-4c6a-4454-a11d-bf785d5bfd4f)

![Screenshot from 2024-11-29 12-34-19](https://github.com/user-attachments/assets/55a977b7-fc14-4642-872a-c6e2f04ebe09)


This was done to run upto 5 different types of task as per their demand

# Setup Role based authorization

![Screenshot from 2024-11-29 12-40-53](https://github.com/user-attachments/assets/049280e0-3691-4fc8-a211-aeb24abc415d)

![Screenshot from 2024-11-29 12-45-27](https://github.com/user-attachments/assets/7de52f25-e441-409b-bc0e-8fc213e0f1db)

Create a item role named project_show with pattern of "project.*" and from the job section give it permission of build, configure, read and workspace.

![Screenshot from 2024-11-29 12-54-00](https://github.com/user-attachments/assets/fecfee65-5378-4cc1-966d-5a031d026acd)



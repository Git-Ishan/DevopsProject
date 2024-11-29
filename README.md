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

Create a Global roles named project and give it permisson of project_view.

![Screenshot from 2024-11-29 12-59-09](https://github.com/user-attachments/assets/6152969f-8770-4f79-a794-bd1cb1c3b675)

Add user project in item roles, give it the permission of project_view.

![Screenshot from 2024-11-29 13-02-14](https://github.com/user-attachments/assets/304d455c-38a2-4dac-8eb4-e6941113a26f)

Login from the project user

![Screenshot from 2024-11-29 13-05-39](https://github.com/user-attachments/assets/57cf67a2-fbc1-4c58-8dc3-0df1680de33d)

Now we will observe the project with same patterns

![Screenshot from 2024-11-29 13-08-55](https://github.com/user-attachments/assets/fad86eb4-d34d-4364-b3be-b04e5d72e5b9)

# Create a pipeline to execute a shell script, on git, on scripting task, Monitor disk utlization and send mail if > 80%, Process Management, take inputs, check for errors, cleanup, backup, logging.

![Screenshot from 2024-11-29 13-24-48](https://github.com/user-attachments/assets/3a86ea88-76df-4731-8d45-82c2eb966436)









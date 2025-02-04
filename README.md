# Script to install Jenkins

This script simplifies the installation of Java 17 and Jenkins on Debian-based Linux or macOS systems. It detects the operating system (Debian or macOS) and uses the appropriate package manager (`apt` for Debian, `brew` for macOS) to install the required packages. The script handles prerequisites, adds the Jenkins repository (for Debian), and completes the software installation. By automating these repetitive setup steps, it streamlines the process of configuring an environment for Jenkins.

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

The scripts required to execute the pipeline, including JenkinsFile, bullet.sh, script1.sh, and script2.sh, are available on GitHub.

![Screenshot from 2024-11-29 13-24-48](https://github.com/user-attachments/assets/3a86ea88-76df-4731-8d45-82c2eb966436)

The Jenkins pipeline performs automation in three stages: Git Checkout (cloning the repository), Disk Usage Check (executing script1.sh), and Process Management (executing bullet.sh). It is configured to run hourly and sends failure notifications via email, providing job details and a link to the console output for troubleshooting.

![Screenshot from 2024-11-29 16-33-41](https://github.com/user-attachments/assets/55346e9d-aac6-4041-a878-b329e76fc7c5)

This Bash script monitors system resources by identifying processes consuming the most CPU and memory. It uses ps aux to sort and display the top resource-intensive processes. Additionally, it detects zombie processes (in the "Z" state) with the help of awk, aiding in efficient process management and troubleshooting.

![Screenshot from 2024-11-29 16-36-16](https://github.com/user-attachments/assets/c8886229-390e-433a-b643-5e949c6aa08d)

This Bash script monitors the root directory's disk usage percentage. If usage exceeds 80%, it displays a warning message and exits with an error code. Otherwise, it confirms that disk usage is within safe limits. This proactive method helps administrators manage potential disk space issues effectively.

![Screenshot from 2024-11-29 16-38-12](https://github.com/user-attachments/assets/cd334c68-8138-4b63-b384-6f6eb6b63a78)

This Bash script automates backups with optional compression. It accepts source and destination directories, validates their existence, and creates the destination if necessary. Backups are uniquely timestamped, compressed when the -c flag is used, or simply copied. Operations are logged for tracking, and backups older than 7 days are removed to conserve space, ensuring efficient and dependable data protection.

![Screenshot from 2024-11-29 16-40-21](https://github.com/user-attachments/assets/31254d11-02aa-46ab-80b3-f2f5403d1a63)

# Build Java app and trigger pipeline

This ensures the installation of Java 17 with the specified version.

![Screenshot from 2024-11-29 16-44-08](https://github.com/user-attachments/assets/1402e943-7dce-47c2-9a7f-69bcacb914bd)\

This ensures the installation of Maven 3.9.9

![Screenshot from 2024-11-29 16-45-12](https://github.com/user-attachments/assets/7aa54f3f-a5c1-4ad2-b0eb-f1285bb91d77)

This Jenkins pipeline automates the build, test, and deploy workflow for a Java project. It pulls code from a Git repository, builds it with Maven (skipping tests during packaging), and runs tests with results published using JUnit. The "Deliver" stage executes a deployment script (`deliver.sh`). The pipeline supports branch selection via parameters and triggers builds on GitHub pushes. Configured to use Maven 3.9.9 and Java 17, it enforces a 10-minute timeout for execution. Post-build steps include archiving artifacts, cleaning the workspace, and logging the pipeline status (success or failure). This setup ensures streamlined, automated, and reliable builds with integrated testing and deployment.

![Screenshot from 2024-11-29 16-49-22](https://github.com/user-attachments/assets/6fa8b976-3da0-4f10-94f1-8a140cb11292)

The Jenkins pipeline now includes the GitHub repository and allows branch selection via a parameter.

![Screenshot from 2024-11-29 16-53-28](https://github.com/user-attachments/assets/45806a7b-6417-4cce-9df4-ffd35ba85bd9)

In the pipeline section, set the definition to Pipeline script from SCM, specifying the Git repository and using */main as the branch specifier.

![Screenshot from 2024-11-29 16-55-13](https://github.com/user-attachments/assets/8b309135-58a5-4ad1-b272-1c461b977f06)

The script path is specified as example-app-pipeline/Jenkinsfile, where the pipeline script is executed from.

![Screenshot from 2024-11-29 16-56-30](https://github.com/user-attachments/assets/709d05ba-b62d-41e9-b444-052dc86dc680)






















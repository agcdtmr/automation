# Jenkins Intermediate

For this Intermediate Jenkins, I followed Linkedin Learning [Jenkins Essential Training](https://www.linkedin.com/learning/jenkins-essential-training-17420152).

## Notes

- [ ] DevOps
- [ ] Planning, Development and Operation
- [ ] DevOps Life Cycle: Plan, Code, Build, Test, Release, Deploy, Operate, Monitor
- [ ] Development Group: Plan, Code, Build, Test
- [ ] Operations Group: Release, Deploy, Operate, Monitor
- [ ] Jenkins is the perfect tool for automating processes, tied to the build, test, release and deploy stages.
- [ ] Continuous integration or CI = build and test phases of the DevOps Life Cycle = produce an artifact that can be deployed.
- [ ] Tools like Jenkins are used to automate the build and test stages, the process is known as continuous integration. Using automation in the release and deploy stages is called continuous delivery. And if the process is completely automated, it can be referred to as continuous deployment.
- [ ] Continuous delivery and deployment or CD = release and deploy stages of the DevOps Life Cycle = take an artifact and make it available for use, or actually put it to work. 
- [ ] The release stage is where the delivery happens. Jenkins may upload a container image to a repository, or make a jar file available for downloading. Ultimately, delivering the artifact means that a version of the application is available and ready to be used. 
- [ ] The next step is to deploy. In some cases the deployment is manual. For a continuous deployment, all steps are automated and completed with no, or very little human interaction.
- [ ] Ubuntu server
- [ ] NGINX
- [ ] proxy
- [ ] web hooks
- [ ] trigger jobs
- [ ] elastic IP
- [ ] DNS
- [ ] EC2 Instance
- [ ] user data script

## Challenge #1: deploying a Jenkins server to use for this course. 

- Challenge: https://github.com/agcdtmr/essential-jenkins-2468076/tree/main/Ch01/01_02-challenge-deploy-a-jenkins-server
- Solution: https://github.com/agcdtmr/automation/tree/main/jenkins-intermediate/challenge01

Requirements for this challenge:
- [x] Use the latest version of Ubuntu Server. 
- [x] Install NGINX as a proxy to Jenkins. 
- [x] Install and configure Jenkins. 
- [x] use a public cloud service for this challenge.

For my solution:
- [x] I used Microsoft Azure
- [x] Linux (ubuntu 20.04), Standard B1s (1 vcpu, 1 GiB memory), 20.4.1.111
- [x] DNS: jenk.westeurope.cloudapp.azure.com
- [x] creates ssh key pair and public as .pem file
- [x] location: West Europe
- [x] nginx version: nginx/1.18.0 (Ubuntu)
- [x] jenkins -version 2.428
- [x] security rules for: ssh 22 (to connect to the server), http 80 (to connect github and jenkins via a web interface)
- [x] uses user data script to install nginx & jenkins


The main reason to use a cloud service is so your Jenkins is accessible from a public URL. In later lessons, we'll be implementing continuous integration from a code repo, and your Jenkins server needs to be publicly accessible to allow a web hook to trigger jobs. 


## Error fixing: To connect to an Ubuntu virtual machine (VM) in Azure using SSH and a `.pem` file, you can follow these steps:

1. **Prepare Your Azure VM**:
   Ensure you have created an Ubuntu VM in Azure and have downloaded the `.pem` private key file during the VM creation process.

2. **Open a Terminal or Command Prompt**:
   Open your local terminal or command prompt. If you're using Windows, you can use the Windows Subsystem for Linux (WSL) or an SSH client like PuTTY.

3. **Set Permissions for the `.pem` File**:
   Make sure the `.pem` file is protected and only readable by you. You can use the `chmod` command on Linux/Mac or simply adjust file properties on Windows.

   ```bash
   chmod 400 /path/to/your/ssh.pem
   ```

4. **SSH into the Azure VM**:
   Use the `ssh` command to connect to your VM. The command will typically look like this:

   ```bash
   ssh -i /path/to/your/ssh.pem username@azure-vm-public-ip
   ```

   - Replace `/path/to/your/ssh.pem` with the full path to your `.pem` file.
   - Replace `username` with the username you created when setting up your Azure VM.
   - Replace `azure-vm-public-ip` with the public IP address or hostname of your Azure VM.

   For example, if your username is "azureuser" and the public IP is "123.45.67.89," the command might look like:

   ```bash
   ssh -i /path/to/your/ssh.pem azureuser@123.45.67.89
   ```

5. **Enter the Passphrase (if Applicable)**:
   If your private key is protected with a passphrase, you'll be prompted to enter it.

6. **You're Now Connected**:
   You should now be connected to your Azure VM via SSH. You can execute commands on the VM through the terminal. When you're finished, simply type `exit` to disconnect.

Please note that the exact commands and filenames may vary depending on your specific setup and file locations. Make sure to replace placeholders with your actual file paths and credentials.

Additionally, ensure that your Azure VM's network security group allows incoming SSH traffic on port 22, and that the VM is running and reachable with the provided public IP address or DNS hostname.


## Error fixing: a virtual machine (VM) running Jenkins and Nginx on Azure, and experiencing issues with DNS or the public IP not working in a browser.s 

**Solution: Adjust NSG or firewall inbound rules for http & https**

Here are some common troubleshooting steps to help you identify and resolve the issue:

1. **Check VM Status:** Ensure that your Azure VM is running and in a healthy state. If it's not running, start the VM from the Azure Portal.

2. **Security Group Rules:** Verify that your Azure Network Security Group (NSG) or firewall rules allow incoming traffic on the necessary ports (e.g., port 80 for HTTP and port 443 for HTTPS). You need to open these ports to allow web traffic to your VM. Check the NSG rules associated with your VM's network interface.

3. **DNS Configuration:** Confirm that your DNS records are correctly configured. If you are using a custom domain, make sure the DNS records (A records or CNAME records) point to the correct public IP address or DNS name associated with your Azure VM.

4. **Public IP Configuration:** Check that the public IP address associated with your VM is correctly assigned and not in a "Reserve" state.

5. **Web Server Configuration:** Ensure that both Jenkins and Nginx are properly configured and running on your VM. Test each service individually by accessing them via their respective ports (e.g., Jenkins on port 8080, Nginx on port 80). Make sure there are no errors in the service configurations.

6. **Firewall Inside VM:** Check the firewall settings inside the VM. Ensure that there are no software firewalls (like UFW on Linux) blocking incoming traffic on the required ports. You may need to adjust firewall rules within the VM.

7. **Nginx Configuration:** If you're using Nginx as a reverse proxy, verify that the Nginx configuration is correctly set up to forward incoming HTTP requests to the Jenkins service. The Nginx server block (virtual host) should be properly configured.

8. **Browser Cache:** Clear your browser cache and try accessing the site again. Sometimes, cached data can interfere with the loading of a website.

9. **Test with IP Address:** If DNS issues persist, try accessing your site directly using the public IP address rather than the domain name. This will help you determine if the issue is DNS-related.

10. **Azure Diagnostics:** Check Azure's diagnostics and monitoring tools for any specific errors or issues related to your VM, public IP, or network configurations.

11. **Logs and Error Messages:** Examine the logs and error messages on your VM, Jenkins, and Nginx for any clues as to what might be causing the issue. These logs can provide valuable information for troubleshooting.


## Bash script for automating the installation and configuration of various software components and services. Here's a short explanation of what's happening in the script:

1. The script begins with a comment and an echo statement to indicate that the installation is starting.

2. It adds the Jenkins package repository key to the system's keyring and sets up the Jenkins repository in the APT sources list.

3. Then, it updates the APT package list and upgrades installed packages.

4. It installs several packages, including Java 11, NGINX, and Jenkins, which are common components for setting up a Jenkins server.

5. The script configures Jenkins by setting options to skip the installation wizard and downloading a list of suggested plugins.

6. It downloads a plugin installation tool, runs it to install the suggested plugins, and changes the ownership of the plugin directory to the Jenkins user.

7. NGINX is configured to act as a reverse proxy for Jenkins, with a new server block defined to pass requests to the Jenkins server.

8. The script reloads NGINX to apply the new configuration.

9. Docker is installed, with the script adding the Docker repository key and setting up the Docker repository in the APT sources list. Docker and related packages are then installed.

10. The Docker and Containerd services are enabled, and the script adds the "ubuntu" and "jenkins" users to the "docker" group.

11. Jenkins is restarted to apply any changes, and the script copies the initial admin password for Jenkins.

12. The script clears the terminal, displays a message that the installation is complete, and provides the initial credentials (username: admin, password: generated during Jenkins setup).

In summary, the script automates the installation and configuration of Jenkins, NGINX, Java, and Docker on a server, making it easier to set up a Jenkins server for continuous integration and continuous deployment (CI/CD) purposes.


## What is apt and apt package list?

`apt` stands for "Advanced Package Tool," and it is a package management system used in various Linux distributions, including Debian, Ubuntu, and their derivatives. `apt` is a command-line tool that allows users to interact with the system's package repositories to install, update, upgrade, and manage software packages.

Here are some common `apt` commands:

1. `apt update`: This command refreshes the local package database by downloading the latest package information from the configured software repositories. It ensures that your system is aware of the most up-to-date package versions available.

2. `apt upgrade`: This command installs the latest versions of all installed packages on your system. It doesn't install new packages or remove any existing ones.

3. `apt-get install <package-name>`: This command is used to install a specific package or packages on your system.

4. `apt-get remove <package-name>`: This command is used to remove a specific package from your system.

5. `apt-get purge <package-name>`: This command is used to remove a package along with its configuration files.

6. `apt list`: This command lists all available packages in the repositories.

7. `apt search <search-term>`: This command allows you to search for packages based on a keyword or search term.

The "APT package list" typically refers to the list of available software packages in the repositories that `apt` uses to manage packages on your system. When you run `apt update`, it downloads and updates this package list to ensure that your system has the latest information about available software packages. This list includes package names, versions, dependencies, and other metadata necessary for package management.

By keeping the APT package list up to date, you can ensure that you are installing and updating software with the most current versions and that you have access to the latest security updates and bug fixes.


## Docker is included in the script provided for several reasons:

Docker is included in the script for several reasons:

1. **Isolation of Jenkins and its Dependencies:** Docker provides a way to isolate Jenkins and its dependencies in a container. This isolation ensures that Jenkins runs consistently, regardless of the underlying system's configuration. It helps prevent conflicts between Jenkins and other software installed on the server.

2. **Ease of Deployment:** Using Docker makes it easy to deploy Jenkins as a containerized application. You can package Jenkins and its required components in a Docker image, making it simple to replicate the same environment on different servers or in different environments (e.g., development, testing, production).

3. **Portability:** Docker containers are highly portable. You can move a Jenkins Docker container between different hosts or cloud platforms without worrying about compatibility issues. This portability is especially valuable in cloud and DevOps environments.

4. **Version Control and Rollbacks:** Docker images can be version-controlled, allowing you to track changes to your Jenkins environment over time. If an update or configuration change causes issues, you can roll back to a previous image.

5. **Consistency:** Docker containers ensure that Jenkins runs consistently across different stages of the software development and deployment lifecycle, which is crucial for maintaining a reliable CI/CD pipeline.

6. **Resource Management:** Docker provides resource management and scaling capabilities, allowing you to allocate specific resources to Jenkins containers, which can help optimize the performance of your Jenkins server.

In summary, Docker is used in the script to containerize Jenkins, making it easier to manage, deploy, and ensure consistent performance of Jenkins within the context of continuous integration and continuous deployment (CI/CD) pipelines. It's a common practice to use Docker for CI/CD environments to maintain a high degree of flexibility, portability, and ease of management.
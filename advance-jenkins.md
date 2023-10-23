# Intermediate Jenkins

For this Intermediate Jenkins, I followed Linkedin Learning [Jenkins Essential Training](https://www.linkedin.com/learning/jenkins-essential-training-17420152).

## Challenge #1: deploying a Jenkins server to use for this course. 

- Challenge: https://github.com/agcdtmr/essential-jenkins-2468076/tree/main/Ch01/01_02-challenge-deploy-a-jenkins-server
- Solution: https://github.com/agcdtmr/automation/tree/main/jenkins-intermediate/challenge01

Requirements for this challenge:

- Use the latest version of Ubuntu Server. 
- Install NGINX as a proxy to Jenkins. 
- Install and configure Jenkins. 
- use a public cloud service for this challenge. For this I used Microsoft Azure:
-- Linux (ubuntu 20.04)
--------- Standard B1s (1 vcpu, 1 GiB memory)
--------- 20.4.1.111
--------- jenk.westeurope.cloudapp.azure.com
--------- creates ssh key as .pem file
--------- location: West Europe
--------- nginx version: nginx/1.18.0 (Ubuntu)
--------- jenkins -version 2.428
--------- security rules for: ssh 22, http 80, https 443


The main reason to use a cloud service is so your Jenkins is accessible from a public URL. In later lessons, we'll be implementing continuous integration from a code repo, and your Jenkins server needs to be publicly accessible to allow a web hook to trigger jobs. 


## To connect to an Ubuntu virtual machine (VM) in Azure using SSH and a `.pem` file, you can follow these steps:

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

If you continue to experience issues, consider providing more specific details about the problem or any error messages you encounter, which would help in providing a more targeted solution.

**Solution: Adjust NSG or firewall inbound rules for http & https**

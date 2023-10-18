# learn-jenkins

## Types of jobs and roles that commonly use Jenkins:

Software Developers: to automate the building, testing, and deployment of their applications. It helps developers catch and fix issues early in the development process.

DevOps Engineers: to automate the deployment of software, manage infrastructure as code, and coordinate various aspects of the software development lifecycle.

System Administrators: server provisioning, backups, and monitoring.

Quality Assurance (QA) Teams: to automate test suites and regression testing, ensuring that software is thoroughly tested before release.

IT Operations Teams:log monitoring, security scans, and patch management.

Release Managers: help manage the release and deployment of software, coordinating the process across different environments.

Product Managers: to schedule and automate data backups, data exports, or other tasks related to product management.

Data Engineers: used for automating data processing tasks, ETL (Extract, Transform, Load) processes, and data pipeline management.

Network Administrators: configuration changes, network monitoring, and security checks.

Build and Release Engineers: for creating the build pipeline, automating software releases, and ensuring the deployment process is smooth and error-free.

Security Teams: for automating security scans and vulnerability assessments in software projects.

Cloud Engineers: can be integrated with cloud platforms like AWS, Azure, and Google Cloud to automate cloud resource provisioning and management.

Database Administrators: Automating database backups, migrations, and maintenance tasks using Jenkins.

Content Management: to automate content publishing and management tasks for websites and content platforms.

Education and Training: Some educators and trainers use Jenkins for teaching purposes, demonstrating how automation can improve workflow and productivity.


## Creating SSH key and adding to ssh-agent and add the new ssh key to gihub account

## Cloning the forked learning-jenkins repo

It seems that there might be an issue with your SSH key configuration and Git is unable to find the SSH key or the SSH configuration file. Let's address this issue step by step:

1. **SSH Key and Configuration File Paths:**
   First, make sure that your SSH key (`id_ed25519`) and your SSH configuration file (`config`) are in the correct locations. Typically, your SSH key should be in `~/.ssh/id_ed25519`, and your SSH configuration file should be in `~/.ssh/config`. You can use the following commands to check if they exist in the right locations:

   ```bash
   ls -l ~/.ssh/id_ed25519
   ls -l ~/.ssh/config
   ```

   If these files don't exist, you need to create them or move your SSH key to the right location. If you're using a different key file, replace `id_ed25519` with the correct filename.

2. **Create SSH Configuration File (if it doesn't exist):**
   If your SSH configuration file doesn't exist, you can create it with a text editor. For example, you can use the `nano` text editor to create the file:

   ```bash
   nano ~/.ssh/config
   ```

   In the `config` file, you can specify the configuration for your SSH key. Here's a basic example:

   ```
   Host github.com
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_ed25519
   ```

   Save the file and exit the text editor.

3. **Correct SSH Key Permissions:**
   Ensure that your SSH key and SSH configuration file have the correct permissions. You can set the correct permissions using the following commands:

   ```bash
   chmod 600 ~/.ssh/id_ed25519
   chmod 600 ~/.ssh/config
   ```

4. **SSH Agent and Key Addition:**
   Make sure your SSH key is added to the SSH agent. You can add your key to the SSH agent using the following command:

   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

5. **Check GitHub SSH Key:**
   Ensure that the SSH public key associated with your SSH private key (`id_ed25519.pub`) is added to your GitHub account. You can do this by going to your GitHub account settings and adding the public key.

6. **Test SSH Connection:**
   After checking the above steps, you can test your SSH connection to GitHub using the following command:

   ```bash
   ssh -T git@github.com
   ```

   If everything is set up correctly, GitHub should acknowledge your connection.

After following these steps, you should be able to use SSH to access your GitHub repositories without encountering the "Permission denied" error. If you continue to experience issues, double-check your SSH key setup and configuration, and ensure that it matches your GitHub account settings.

Error fixing:

- First I was trying to clone the main repo and not the one I forked.


- [ ] https://www.jenkins.io/doc/
- [ ] https://www.cloudbees.com/jenkins/what-is-jenkins
- [ ] https://www.linkedin.com/learning/learning-jenkins-14423877/exercise-files?autoSkip=true&resume=false&u=2080948
- [ ] https://www.jenkins.io/doc/book/installing/docker/
- [ ] https://www.macminivault.com/installing-jenkins-on-macos/
- [ ] https://medium.com/javarevisited/7-best-courses-to-learn-jenkins-and-ci-cd-for-devops-engineers-and-software-developers-df2de8fe38f3
- [ ] https://www.knowledgehut.com/blog/devops/what-is-jenkins
- [ ] https://www.javatpoint.com/jenkins
- [ ] https://www.edx.org/learn/computer-science/the-linux-foundation-introduction-to-jenkins
- [ ] https://phoenixnap.com/kb/what-is-jenkins
- [ ] https://www.edureka.co/blog/what-is-jenkins/
- [ ] https://learn.microsoft.com/en-us/azure/developer/jenkins/
- [ ] https://www.lambdatest.com/blog/what-is-jenkins/
- [ ] https://www.simplilearn.com/tutorials/jenkins-tutorial
- [ ] https://www.tutorialspoint.com/jenkins/index.htm
- [ ] https://codefresh.io/learn/jenkins/
- [ ] https://www.spiceworks.com/tech/devops/articles/what-is-jenkins/
- [ ] https://hub.docker.com/_/jenkins/
- [ ] https://www.techtarget.com/searchsoftwarequality/definition/Jenkins
- [ ] https://www.infoworld.com/article/3239666/what-is-jenkins-the-ci-server-explained.html



Gitlab
- [ ] https://about.gitlab.com/solutions/jenkins/

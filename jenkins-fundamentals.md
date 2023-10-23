# jenkins-fundamentals

Steps taken:
- [x] Follow Linkedin Learning course about [Jenkins Fundamentals](https://www.linkedin.com/learning/learning-jenkins-14423877) sponsored by the company. 
- [x] Create ssh keys, add to ssh-agent and add to github (I needed to do this first because the linkedin learning uses github for its course module).
- [x] Forking the [module](https://github.com/LinkedInLearning/learning-jenkins-3003221) and cloning that forked repo locally.
- [x] Fork the repo with all branches. (The modules are pushed in different branches)
- [x] Install Homebrew
- [x] Install Git
- [x] Install Java
- [x] Install Jenkins
- [x] Reinstalling VSCode and fixing related error (I need this to have a better access to different branches)
- [x] Installing Docker and setting up the environment
- [x] Successfully finished the course quizzes, [modules](https://github.com/LinkedInLearning/learning-jenkins-3003221) and mini projects. Check my certificate [here](https://github.com/agcdtmr/learn-jenkins/blob/main/CertificateOfCompletion_Learning%20Jenkins.pdf).
- [x] Look at the mini [jenkins projects](https://github.com/agcdtmr/learn-jenkins/tree/main/images).
- [x] Create .gitignore file
- [x] Pause jenkins container on Docker and because I first used jenkins locally I also needed to stop that jenkins service using homebrew.

## Terminology

- jenkins
- automation
- openjdk
- container
- sudo
- root user
- plugins
- maven
- job
- build
- build step
- string parameter
- choice parameters
- boolean parameter
- cron or cron jobs
- pipeline as code
- regular expression
- stage

## why i need java when installing jenkins?

Jenkins is a popular open-source automation server that is primarily used for automating software development and deployment processes. Java is required when installing Jenkins for several reasons:

1. Jenkins is built on Java: Jenkins itself is a Java-based application. It is a Java servlet container that runs as a web application on a Java Virtual Machine (JVM). To run Jenkins, you need to have Java installed on your server.

2. Plugins and Extensions: Jenkins has a vast ecosystem of plugins and extensions that enhance its functionality. Many of these plugins are also written in Java. Java provides the runtime environment for these plugins to execute within the Jenkins server.

3. Cross-platform Compatibility: Java is known for its platform independence, which means Jenkins can be run on various operating systems, such as Windows, Linux, and macOS, as long as a compatible Java runtime is available.

4. Stability and Performance: Java's memory management and runtime environment help ensure the stability and performance of Jenkins. It allows Jenkins to handle continuous integration and continuous delivery tasks efficiently.

5. Security: Java provides security features that are essential for running server applications like Jenkins. Java has built-in security mechanisms to control and manage access to the Jenkins server and its resources.

To install Jenkins, you typically need to install Java first and make sure it is properly configured on your system. Jenkins provides installation packages for different operating systems, and these packages often come bundled with a specific version of Java to ensure compatibility. However, it's essential to ensure that you have the correct version of Java installed to run Jenkins effectively.

In summary, Java is a fundamental requirement for running Jenkins because it is the underlying technology on which Jenkins is built, and it provides the necessary runtime environment and compatibility for Jenkins to operate effectively.

## Creating SSH key and adding to ssh-agent and add the new ssh key to gihub account

To create an SSH key, add it to your `ssh-agent`, and then add the key to your GitHub account, follow these steps:

1. **Generate an SSH Key:**

   On your local machine, open a terminal or command prompt and generate an SSH key using the `ssh-keygen` command. Replace `your_email@example.com` with your GitHub-associated email address.

   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   You can also use the `-t rsa` option if you prefer RSA keys, but it's recommended to use ed25519 for better security.

   The command will prompt you to choose a location to save the key, and you can press Enter to use the default location (`~/.ssh/id_ed25519`).

2. **Start the ssh-agent:**

   If you're using macOS or Linux, you can start the `ssh-agent` as follows:

   ```bash
   eval "$(ssh-agent -s)"
   ```

   If you're using Windows, you can use the Git Bash terminal or PowerShell, and the `ssh-agent` should be started automatically when you install Git.

3. **Add Your SSH Key to ssh-agent:**

   Add your SSH key to the `ssh-agent` using the `ssh-add` command. If you used a different filename for your SSH key, replace `~/.ssh/id_ed25519` with the path to your SSH private key file.

   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

4. **Copy Your SSH Public Key:**

   Use the following command to copy the public key to your clipboard. Replace `~/.ssh/id_ed25519.pub` with the path to your public key if it's different.

   ```bash
   pbcopy < ~/.ssh/id_ed25519.pub  # macOS only
   ```

   If you're on Windows or using a different clipboard manager, you may need to manually copy the contents of `~/.ssh/id_ed25519.pub`.

5. **Add Your SSH Key to GitHub:**

   - Log in to your GitHub account.
   - Click on your profile picture in the upper-right corner and go to "Settings."
   - In the left sidebar, click on "SSH and GPG keys."
   - Click the "New SSH key" button.
   - Give your SSH key a title (e.g., "My SSH Key") and paste the copied public key into the "Key" field.
   - Click "Add SSH key."

Your SSH key is now added to your GitHub account, and you can use it to authenticate when interacting with GitHub repositories. Make sure you keep your private key secure and do not share it with others.

## Cloning the forked learning-jenkins repo

The was an issue with my SSH key configuration and Git is unable to find the SSH key or the SSH configuration file while I'm checking if the forking/cloning was successful. I address this issue step by step:

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


## Error fixing: Other branch from the original repo not showing locally

First I was trying to clone the main repo and not the one I forked.

How to fork a repo with all the branches

When you fork a repository on GitHub, it doesn't automatically fork all of the branches. By default, a fork of a repository will only contain the default branch (usually "main" or "master"). However, you can fork individual branches from the original repository into your fork. Here's how you can do it:

1. **Fork the Repository:**
   First, fork the repository you're interested in. Go to the repository on GitHub and click the "Fork" button in the top right corner. This will create a copy of the repository in your GitHub account.

2. **Clone Your Fork:**
   After forking, clone your forked repository to your local machine using the `git clone` command. Replace `<your-fork-url>` with the URL of your forked repository:

   ```bash
   git clone <your-fork-url>
   ```

3. **Add the Original Repository as a Remote:**
   To fetch branches from the original repository, you need to add it as a remote. Replace `<original-repo-url>` with the URL of the original repository:

   ```bash
   git remote add upstream <original-repo-url>
   ```

4. **Fetch All Branches from the Original Repository:**
   To fetch all branches from the original repository, use the following command:

   ```bash
   git fetch upstream
   ```

   This will fetch all branches from the original repository into your local fork.

5. **Checkout a Branch from the Original Repository:**
   Once you've fetched the branches, you can check out a branch from the original repository to work on it. For example, if you want to work on a branch named `feature-branch`:

   ```bash
   git checkout -b feature-branch upstream/feature-branch
   ```

   This will create and switch to a new branch in your local fork that is based on the `feature-branch` from the original repository.

6. **Push the New Branch to Your Fork:**
   After making changes to the branch, you can push it to your fork on GitHub:

   ```bash
   git push origin feature-branch
   ```

   This will make the changes available in your fork on GitHub.

Repeat the process for each branch you want to fork from the original repository. By adding the original repository as a remote and fetching its branches, you can work on any branch from the original repository within your fork.

## Understanding Exit 1 and Exit 0

The instructor introduced an error while running a Jenkins job to show how a failure job looks like using the dashboard. I do understand the first and second line od code below. But the exit 1 not.

```
#!/bin/bash
for i in {1..30}; do echo $i; sleep 1; done
exit 1
```

In most Unix-like operating systems, including Linux and macOS, the exit status of a program or script is represented by an integer value, which is returned when the program or script terminates. By convention, a return status of 0 signifies success, and any non-zero status code typically indicates an error or failure.

This convention allows other programs or scripts that call your script to check its exit status and determine whether it completed successfully or encountered a problem. The exact meaning of non-zero exit codes can vary depending on the program or script, and it is up to the developer to define these meanings. However, a non-zero exit status is generally used to indicate that something went wrong or an error occurred during execution.

For example, in your original script, you used `exit 1` to indicate a failure. This is a common practice where a non-zero exit code (in this case, 1) is used to signal that the script did not complete successfully.

By using this convention, Jenkins and other automation tools can easily determine whether a build or job was successful or not. If a build step returns a non-zero exit code, Jenkins interprets it as a failure, making it easier to identify and manage issues in your automation pipeline.


## Error fixing: `code .` command to open the code/file on vscode not working.

```
code .
zsh: command not found: code
```

1. Uninstalled VSCode.
2. Reinstall VSCode.

The error message you're seeing, "zsh: command not found: code vscode," suggests that the "code" command is not recognized by your Zsh shell. This typically happens when Visual Studio Code (VSCode) is not added to your system's PATH or if VSCode is not installed.

Here are a few steps to resolve this issue:

1. Verify that Visual Studio Code is installed:
   Make sure that Visual Studio Code is installed on your system. You can download it from the official website: https://code.visualstudio.com/

2. Add VSCode to your PATH:
   If you've installed Visual Studio Code but it's not in your PATH, you won't be able to run it from the command line. You can add it to your PATH by modifying your shell profile configuration.

   For Zsh, you can add the following line to your `~/.zshrc` file:

   ```bash
   export PATH="$PATH:/path/to/VSCode.app/Contents/Resources/app/bin"
   ```

   Replace "/path/to/VSCode.app" with the actual path to your VSCode installation. You can usually find VSCode in the "Applications" directory on macOS.

3. Restart your Zsh shell:
   After making changes to your shell configuration, you'll need to restart your Zsh session or run `source ~/.zshrc` to apply the changes.

4. Test the "code" command:
   After you've added VSCode to your PATH and restarted your shell, you should be able to use the "code" command to open Visual Studio Code from the command line.

If you're still facing issues, double-check that Visual Studio Code is correctly installed, and that you've added the correct path to your shell configuration. Additionally, make sure there are no typos in the command you're trying to run.


```
EACCES: permission denied, unlink '/usr/local/bin/code'
```


The error message "EACCES: permission denied, unlink '/usr/local/bin/code'" indicates that you don't have the necessary permissions to remove or unlink the "code" binary from the "/usr/local/bin" directory, which is where VSCode is typically installed when you use the command-line installation method.

To resolve this issue, you can use the "sudo" command to execute the "unlink" operation with elevated privileges. Here's how you can do it:

1. Open your terminal.

2. Use the "sudo" command to remove the "code" binary:

   ```bash
   sudo unlink /usr/local/bin/code
   ```

3. You might be prompted to enter your administrator password to confirm the action.

4. Once the unlink operation is successful, you should be able to reinstall or update Visual Studio Code without permission issues.

After unlinking, you can proceed with reinstalling or updating Visual Studio Code. If you encounter any issues during the installation or updating process, you may want to use "sudo" for those operations as well. However, use caution when using "sudo" and make sure you trust the source of the installation to avoid security risks.

When I followed [this](https://www.freecodecamp.org/news/how-to-open-visual-studio-code-from-your-terminal/) again.
A prompt pop-out "Code will now prompt with 'osascript' for Administrator privileges to install the shell command.". Then I entered the password. After following all the instructions above I was able to fix the error on the terminal, and now can use `code .` command to open code/file from terminal to vscode easily.


## Error fixing: maven and java incompatibility

```
Downloaded from central: https://repo.maven.apache.org/maven2/com/thoughtworks/qdox/qdox/2.0-M9/qdox-2.0-M9.jar (317 kB at 1.2 MB/s)
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/.jenkins/workspace/Hello-Maven/target/classes
[INFO] -------------------------------------------------------------
[ERROR] COMPILATION ERROR : 
[INFO] -------------------------------------------------------------
[ERROR] Source option 7 is no longer supported. Use 8 or later.
[ERROR] Target option 7 is no longer supported. Use 8 or later.
[INFO] 2 errors 
[INFO] -------------------------------------------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  6.313 s
[INFO] Finished at: 2023-10-19T10:34:37+02:00
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.8.0:compile (default-compile) on project hello: Compilation failure: Compilation failure: 
[ERROR] Source option 7 is no longer supported. Use 8 or later.
[ERROR] Target option 7 is no longer supported. Use 8 or later.
[ERROR] -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoFailureException
Build step 'Invoke top-level Maven targets' marked build as failure
Finished: FAILURE
```

What the error above means? The error message you're encountering is related to the Java version compatibility settings in your Maven project. The error message is saying that "Source option 7 is no longer supported. Use 8 or later" and "Target option 7 is no longer supported. Use 8 or later."

Solutions:

- to match your OpenJDK 21 (Java 16) version:

1. Open your project's Maven `pom.xml` file using a text editor or an Integrated Development Environment (IDE) that supports Maven.

2. Locate the `<build>` section in your `pom.xml` file. If it doesn't exist, you can add it within the `<project>` section. Here's an example of where to place it:

   ```xml
   <project>
       <!-- ... other project settings ... -->
       <build>
           <!-- ... plugin configuration ... -->
       </build>
   </project>
   ```

3. Within the `<build>` section, you need to configure the `maven-compiler-plugin`. If it's not already there, you can add it as shown below:

   ```xml
   <build>
       <plugins>
           <plugin>
               <groupId>org.apache.maven.plugins</groupId>
               <artifactId>maven-compiler-plugin</artifactId>
               <version>3.8.0</version>
               <configuration>
                   <source>16</source>
                   <target>16</target>
               </configuration>
           </plugin>
       </plugins>
   </build>
   ```

   Make sure that you replace the `<source>` and `<target>` values with "16" to match your OpenJDK 21 version.

4. Save the `pom.xml` file.

5. Once you've saved the `pom.xml`, you can try building your project again using Maven. The error you encountered should be resolved.

These steps update your project's Java source and target compatibility levels to match your installed Java version, OpenJDK 21 (Java 16). This should allow Maven to compile your project without issues related to outdated compatibility settings.

- I was first using and running Jenkins locally. But because I don't have the right to push to the code base, I won't be able to use solution above. Now I will try to run it using a container / docker.

**Update: The docker environment was successfully configured. I noticed that on 03_01 "Using a global tool" module, the instructor used Maven 3.8.2 so I used that to not have any conflict anymore from the given github account.**


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



## Sources

Jenkins
- [ ] https://www.jenkins.io/doc/
- [ ] https://www.cloudbees.com/jenkins/what-is-jenkins
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

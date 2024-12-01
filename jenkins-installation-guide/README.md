
# Jenkins Installation Guide for Kali Linux

This guide walks you through the process of installing Jenkins on Kali Linux. Follow these steps to get Jenkins running on your system.

## Prerequisites

- **Kali Linux** (or any Debian-based system).
- **Root privileges** or **sudo access** to execute commands.

## Steps to Install Jenkins on Kali Linux

### Step 1: Update System Packages

First, update your package repository to ensure all packages are up to date:

```bash
sudo apt-get update
```

### Step 2: Install Required Dependencies

Jenkins requires Java to run. Install Java Runtime Environment (JRE) and other dependencies:

```bash
sudo apt-get install fontconfig openjdk-17-jre
```

Then, install Jenkins:

```bash
sudo apt-get install jenkins
```

### Step 3: Configure Jenkins to Use Java

After Jenkins installation, you need to configure the `JAVA_HOME` environment variable to point to the Java directory.

Edit the Jenkins configuration file:

```bash
sudo nano /etc/default/jenkins
```

In the file, add the following line under the `JAVA_ARGS` section:

```bash
JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
```

### Step 4: Save and Exit the File

- Press **Ctrl + O** to save the changes.
- Press **Ctrl + X** to exit the editor.

### Step 5: Restart Jenkins Service

Now that the `JAVA_HOME` is set, restart Jenkins to apply the changes:

```bash
sudo systemctl restart jenkins
```

### Step 6: Access Jenkins Web Interface

After restarting Jenkins, you can access the Jenkins web interface on your browser:

```bash
http://localhost:8080
```

### Step 7: Retrieve the Jenkins Unlock Password

To unlock Jenkins, you will need the initial admin password. Run the following command to get the password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

### Step 8: Unlock Jenkins

Copy the password from the terminal and paste it into the Jenkins unlock page at `http://localhost:8080`.

### Step 9: Complete the Setup

After unlocking Jenkins, follow the on-screen instructions to complete the setup. Provide your basic details and set up the first admin user.

---

## Conclusion

You should now have Jenkins installed and running on your Kali Linux system. You can begin configuring Jenkins for your continuous integration and continuous deployment (CI/CD) pipelines.

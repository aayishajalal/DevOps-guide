
# Docker Installation Guide for Kali Linux

This guide will walk you through the process of installing Docker on Kali Linux, including troubleshooting steps for permission issues and how to use Docker without `sudo`. Follow the steps below to install Docker, and configure your system to work with Docker containers.

## Prerequisites

- **Kali Linux** (or any Debian-based system).
- **Root privileges** or **sudo access** to execute commands.

## Step 1: Update System Packages

Before installing Docker, it is essential to update the package list to ensure your system has the latest updates.

```bash
sudo apt update
```

## Step 2: Install Docker

Since Kali Linux already has a package named `docker`, we need to install `docker.io` instead. This package contains the container version of Docker.

```bash
sudo apt install -y docker.io
```

## Step 3: Enable and Start Docker

After installation, enable Docker to start on boot and start the Docker service immediately.

```bash
sudo systemctl enable docker --now
```

## Step 4: Verify Docker Installation

Run the following command to check if Docker was successfully installed:

```bash
docker
```

You should see the Docker command-line interface (CLI) output.

## Step 5: Optional - Use Docker Without `sudo`

To use Docker without needing `sudo` every time, add your user to the Docker group:

```bash
sudo usermod -aG docker $USER
```

After adding your user to the Docker group, **log out and log back in** to apply the changes.

## Step 6: Install Docker-CE (Optional)

If you prefer to install the latest Docker Community Edition (docker-ce) from the Docker repository, follow these steps:

### Add Docker Repository to APT Sources

Since Kali Linux is based on Debian, we will add Docker's repository for Debian's stable version (`bookworm`).

```bash
echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian bookworm stable" |   sudo tee /etc/apt/sources.list.d/docker.list
```

### Import Docker GPG Key

Import Docker’s GPG key to authenticate the packages from Docker's repository.

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg |   sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

### Install Docker-CE

After setting up the repository, install the latest version of Docker Community Edition (docker-ce).

```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

## Step 7: Verify Docker-CE Installation

After installation, you can check the installed Docker version:

```bash
docker --version
```

## Step 8: Docker Hub Account

To use Docker Hub for pulling images, you need to create an account on Docker Hub:

- Create an account on [Docker Hub](https://hub.docker.com/).

### Log In to Docker Hub

To log in to Docker Hub from the terminal:

```bash
docker login
```

Enter your Docker Hub username and password.

### Log Out of Docker Hub

To log out from Docker Hub:

```bash
docker logout
```

## Step 9: Resolving Docker Permission Issues

If you encounter the error `Got permission denied while trying to connect to the Docker daemon socket`, follow these steps:

1. Add your user to the Docker group:

   ```bash
   sudo usermod -aG docker $USER
   ```

2. Log out and log back in or restart your system to apply the group changes.

3. Verify Docker runs without `sudo`:

   ```bash
   docker run hello-world
   ```

This should resolve permission issues when using Docker.

---

## Conclusion

You should now have Docker successfully installed and configured on your Kali Linux system. You can start using Docker to run containers and deploy your applications. If you followed the optional steps, you now have the latest version of Docker-CE installed.

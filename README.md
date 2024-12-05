# Docker-on-Instance

This guide provides step-by-step instructions for setting up Docker on a completely new instance. Follow these commands in sequence to install Docker and get it running.

<img alt="image" src="https://github.com/user-attachments/assets/3d753b59-308a-4551-8728-b07ed5aabf8f">

## Prerequisites

Ensure you have a fresh Linux instance (Ubuntu/Debian or similar). You need a user with `sudo` privileges.

---

## Step 1: Update the System Packages

```shell 
sudo apt update && sudo apt upgrade
```

---

## Step 2: Install Required Packages

```shell 
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```

---

## Step 3: Add Docker’s Official GPG Key

```shell 
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

---

## Step 4: Set Up the Docker Repository

```shell 
echo \"deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable\" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

---

## Step 5: Update the Package Database with Docker Packages

```shell 
sudo apt update
```

---

## Step 6: Install Docker

```shell 
sudo apt install docker-ce docker-ce-cli containerd.io -y
```

---

## Step 7: Verify Docker Installation

```shell 
docker --version
```

---

## Step 8: Manage Docker as a Non-Root User (Optional)

1. Add your user to the `docker` group:
   
   ```shell
   sudo usermod -aG docker ${USER}
   ```
   
3. Apply the changes:
   
   ```shell
   newgrp docker
   ```

---

## Step 9: Test Docker Installation

Run the `hello-world` container to verify everything is working correctly.

```shell 
docker run hello-world
```

---

## Step 10: Enable and Start Docker (Optional)

1. Enable Docker to start on boot:
   
   ```shell
   sudo systemctl enable docker
   ```
   
3. Start Docker:
   
   ```shell
   sudo systemctl start docker
   ```

---

## Step 11: Check Docker Status

```shell 
sudo systemctl status docker
```

---

## Step 12: Set Up Docker Compose (Optional)

1. Download Docker Compose:
   
   ```shell
   sudo curl -L \"https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep -oP '\"tag_name\": \"v\K[^\"]*')/docker-compose-$(uname -s)-$(uname -m)\" -o /usr/local/bin/docker-compose
   ```
   
3. Make it executable:
   
   ```shell
   sudo chmod +x /usr/local/bin/docker-compose
   ```
   
5. Verify Docker Compose installation:
   
   ```shell
   docker-compose --version
   ```

---

## Conclusion

You now have Docker installed and running on your new instance. You can start using Docker to build, run, and manage containers.

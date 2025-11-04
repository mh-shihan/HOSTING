# VPS Hosting Guide

This guide provides an overview of VPS (Virtual Private Server) hosting, including setup, management, and best practices.

Follow the links below to navigate to specific sections of the guide or this Readme:

- [First Time Setup Instructions](https://thapatechnical.shop/blogs/host-a-mern-stack-app-on-a-vps)

## First Time Setup Instructions

### 1. Connect to Your VPS:

You can connect to your VPS using SSH. Open a terminal on your local machine and use the following command, replacing <your-username> and <your-vps-ip> with your actual VPS details:

```bash
ssh <your-username>@<your-vps-ip>
```

### 2. Update Your VPS:

Once connected, it's important to update your VPS to ensure you have the latest security patches and software updates. You can do this by running the following commands:

For Debian/Ubuntu-based systems:

```bash
sudo apt update && sudo apt upgrade -y
```

### 3. Install & Upgrade NVM: for the first time for a specific VPS

To install or upgrade Node Version Manager (NVM), you can use the following commands:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

Restart your terminal then the NVM command will be available.

To verify the installation, run:

```bash
nvm --version
```

To install the latest Node.js version, use:

```bash
nvm install --lts
```

### 4. MongoDB Setup

```bash
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor
```

```bash
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
```

```bash
sudo apt-get update
```

```bash
sudo apt-get install -y mongodb-org
```

Check the Status:

```bash
sudo systemctl status mongod
```

```bash
sudo systemctl start mongod
sudo systemctl enable mongod
```

To check VPS operating system details, use:

```bash
lsb_release -a
```

### 5. Install Git

To install Git on your VPS, run the following command:

```bash
sudo apt-get install git -y
```

Install GitHub CLI

```bash
sudo apt install gh -y
```

Login to GitHub

```bash
gh auth login
```

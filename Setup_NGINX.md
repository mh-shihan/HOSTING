# Setup NGINX as a Reverse Proxy

### 1. Install NGINX

```bash
sudo apt-get install nginx -y
```

### 2. Verify NGINX Installation

Go to the NGINX configuration directory:

```bash
cd /etc/nginx
```

### 3. Remove Default Configuration

```bash
cd sites-available
cat default.conf   --> default.conf.bak
```

```bash
 rm default.conf
```

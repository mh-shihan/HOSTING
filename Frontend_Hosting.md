# Frontend Hosting

### 1. Clone the repository

### 2. Install npm

### 3. Create `.env.local` file

```bash
   nano .env.local
```

To check the environment file

```bash
   cat .env.local
```

### 4. Setup NGINX server

```

server {
    listen 80;
    root /root/usr/src/peer-research-lab/peerResarchLabClient/dist;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

Press `CTRL + O` then press `Enter` to save and `CTRL + X` to exit.

To Test NGINX configuration

```bash
   sudo nginx -t
```

### 5. Add symbolic link to site-enabled

```bash
   ln -s ../sites-available/93.127.185.39.conf
```

### 6. Restart NGINX

```bash
   systemctl restart nginx
```

### 7. Copy from ip.conf to domain.com

```bash
   cp ip.conf domain.com.conf
```

```
server {
        listen 80;
        server_name peerresearchlab.com www.peerresearchlab.com;
        root /usr/src/peer-research-lab/peerResarchLabClient/dist;

        location / {
                try_files $uri $uri/ /index.html;
        }
}
```

```bash
   ln -s ../sites-available/peerresearchlab.com.conf
```

### 8. Restart NGINX

```bash
   systemctl restart nginx
```

### 9. Add SSL Certificate

```bash
sudo apt-get install certbot python3-certbot-nginx
```

```bash
sudo certbot --nginx -d mywebsite.com -d www.mywebsite.com
```

```bash
sudo certbot --nginx -d api.mywebsite.com -d www.api.mywebsite.com
```

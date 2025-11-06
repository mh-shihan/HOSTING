## Add SSL Certificate

To secure your application with SSL, you can use Let's Encrypt to obtain a free SSL certificate. Follow these steps:

### 1. Install Certbot

```bash
sudo apt-get install certbot python3-certbot-nginx -y
```

### 2. Obtain SSL Certificate

Run the following command, replacing `<your-domain>` with your actual domain name:

```bash
sudo certbot --nginx -d api.mywebsite.com -d www.api.mywebsite.com
```

sudo certbot --nginx -d api.peerresearchlab.com -d www.api.peerresearchlab.com

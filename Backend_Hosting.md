## Backend Hosting

### 1. Create a folder for your project inside /usr/src

```bash
mkdir my-backend-app
```

### 2. Navigate to the folder

```bash
cd ~/my-backend-app
```

### 3. Clone your repository

```bash
git clone <your-repository-url> .
```

### 4. Install project dependencies

```bash
npm install
or
npm i
```

### 5. Set up environment variables

```bash
nano .env
```

After adding your environment variables, save (`CTRL + O` then `ENTER`) and exit the editor (in nano, press `CTRL + X`, then `Y`, then `ENTER`).

To Check if the environment variables are set correctly, you can use:

```bash
cat .env
```

In this process if any error occurs then the server will shut down. To avoid this you can use Process Manager `pm2` to manage your application.

### 6. Install PM2 to manage your application

```bash
npm install pm2 -g
pm2 start npm --name "my-backend-app" -- run start
```

To Check the details of your application, use:

```bash
pm2 ls
```

To view logs:

```bash
pm2 logs my-backend-app
```

To run the server on Linux:

```bash
curl your-url
```

### 7. Setup NGINX as a Reverse Proxy

Inside NGINX configuration directory: Go to Sites-Available folder and create a new configuration file for your backend application.

```bash
cd /etc/nginx/sites-available
nano my-backend-app.com.conf
```

Add the following configuration:

```bash
server {
        listen 80;
        server_name api.peerresearchlab.com www.api.peerresearchlab.com;

        location / {
                proxy_pass http://localhost:8000;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
        }
}
```

```bash
ln -s ../sites-available/api.peerresearchlab.com.conf
```

Restart NGINX to apply the changes:

```bash
systemctl restart nginx
```

### 8. Add SSL Certificate

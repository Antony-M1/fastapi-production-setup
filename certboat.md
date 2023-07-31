
# What is certboat?

Certbot is usually meant to be used to switch an existing HTTP site to work in HTTPS (and, afterward, to continue renewing the site's HTTPS certificates whenever necessary). Some Certbot documentation assumes or recommends that you have a working web site that can already be accessed using HTTP on port 80.

# Quick Start

**Step 1**

Update System Packages:
Update your system packages to ensure you have the latest software repositories and dependencies:
```
sudo apt update && sudo apt upgrade -y
```

**Step 2**

Install Nginx:
Install the Nginx web server on your EC2 instance:
```
sudo apt install nginx -y
```

**Step 3**

If you already installed Nginx you follow this or else install `Nginx` first
Start Nginx:
Start Nginx and enable it to start on boot:
```
sudo systemctl start nginx
sudo systemctl enable nginx
```

**Step 4**

Install Certbot:
Install Certbot, which is a tool to obtain SSL/TLS certificates from Let's Encrypt:
```
sudo apt install certbot python3-certbot-nginx -y
```

**Step 5**

Obtain SSL/TLS Certificates:
Use Certbot to obtain `SSL/TLS` certificates for your Nginx site. Replace `your-domain.com`
```
sudo certbot --nginx -d your-domain.com
```

**Step 6**

Update Nginx Configuration:
Certbot should have updated your Nginx configuration to use SSL/TLS certificates. You can check the configuration at `/etc/nginx/sites-available/your-domain.com` (for Ubuntu) or `/etc/nginx/conf.d/your-domain.com.conf` (for Amazon Linux).

After changes you have to link in `Sites-enabled` folder
```
sudo ln -s /etc/nginx/sites-available/<SITE_NAME> /etc/nginx/sites-enabled
```

**Step 7**

Reload Nginx:
Reload Nginx to apply the new configuration with SSL/TLS certificates:
```
sudo systemctl reload nginx
```
That's it! You should now have Nginx set up with SSL/TLS certificates obtained from Let's Encrypt using Certbot on your EC2 instance. Your website should be accessible over HTTPS with the SSL/TLS encryption enabled. Remember to keep your certificates updated using Certbot's automatic renewal feature.

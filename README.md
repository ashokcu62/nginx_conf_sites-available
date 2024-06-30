# nginx_conf_sites-available


# Step 1  Installing Node.js

cd ~

# installs nvm (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# download and install Node.js (you may need to restart the terminal)
nvm install 18

# verifies the right Node.js version is in the environment
node -v # should print `v18.20.3`

# verifies the right NPM version is in the environment
npm -v # should print `10.7.0`



##  Step 2 instatll  Nginx 

sudo apt update

sudo apt install nginx 



## Step 3  Setting Up Nginx as a Reverse Proxy Server

sudo systemctl start nginx

sudo systemctl enbale nginx

# restart and check the ngix status
sudo systemctl status nginx 

# Nginx configuration in the /etc/nginx/sites-available/default file. Open the file for editing:

sudo nano /etc/nginx/sites-available/default

/etc/nginx/sites-available/default

use default file from the git repo

# Make sure you didn’t introduce any syntax errors by typing:

sudo nginx -t

# restart Nginx:
sudo systemctl restart nginx




## Step 4 Installing PM2

sudo npm install -g pm2


## Step 5  Managing Applications with PM2

pm2 start "hello.js"  --name frontend  

# react+ vite start 
pm2 start "npm run dev "  --name frontend 


# node express
pm2 start "npx nodemon@latest server.js "  --name backend


# Applications that are running under PM2 will be restarted automatically if the application crashes or is killed, but an additional step needs to be taken to get the application to launch on system startup (boot or reboot). Luckily, PM2 provides an easy way to do this, the startup subcommand.

# The startup subcommand generates and configures a startup script to launch PM2 and its managed processes on server boots:

pm2 startup systemd


# Stop an application with this command (specify the PM2 App name or id)

pm2 stop app_name_or_id

# Restart an application with this command (specify the PM2 App name or id):

pm2 restart app_name_or_id

# More information about a specific application can be found by using the info subcommand (specify the PM2 App name or id):

pm2 info example

# The PM2 process monitor can be pulled up with the monit subcommand. This displays the application status, CPU, and memory usage:

pm2 monit


# source link

https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-16-04#step-5-setting-up-nginx-as-a-reverse-proxy-server
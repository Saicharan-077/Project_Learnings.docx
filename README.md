# My project Learnings 
GIT SETUP AND CLONE

1  Open VS Code and create or open a folder where the project will be placed
2  Initialize Git in the terminal
   Command: git init
3  Add a remote origin to your local repository
   Command: git remote add origin <your-repo-url>
4  Check which origin you are connected to
   Command: git remote
5  Verify the fetch and push URLs
   Command: git remote -v
6  Set global Git username and email
   Command: git config --global user.name "SAI CHARAN"
   Command: git config --global user.email "yourmail@example.com"
7  Rename branch to main if needed
   Command: git branch -m main
8  Pull the existing project from GitHub
   Command: git pull origin main

WARDEN APP SETUP

1  Switch to E Drive where the project is located
   Command: E:
2  Navigate to the warden-app folder
   Command: cd "KP SIR PROJECT\hostel-food\warden-app"
3  Install all required frontend dependencies
   Command: npm install
4  Install cross-env to support environment variables on Windows
   Command: npm install cross-env --save-dev
5  Open package.json to edit the start script
   Command: notepad package.json
6  Change the start script line
   From: "start": "PORT=4000 react-scripts start"
   To:   "start": "cross-env PORT=4000 react-scripts start"
7  Start the Warden React App
   Command: npm start

STUDENT APP SETUP

1  Navigate to student-app folder
   Command: cd "..\student-app"
2  Install all student app dependencies
   Command: npm install
3  Install cross-env if not already installed
   Command: npm install cross-env --save-dev
4  Open package.json to edit start script
   Command: notepad package.json
5  Change the start script line
   From: "start": "PORT=3000 react-scripts start"
   To:   "start": "cross-env PORT=3000 react-scripts start"
6  Start the Student React App
   Command: npm start

BACKEND SERVER SETUP

1  Navigate to backend folder
   Command: cd "..\backend"
2  Install backend dependencies
   Command: npm install
3  Open package.json to edit backend start script
   Command: notepad package.json
4  Change the start script line
   From: "start": "PORT=6201 ts-node src/index.ts"
   To:   "start": "cross-env PORT=6201 ts-node src/index.ts"
5  Install cross-env if not installed
   Command: npm install cross-env --save-dev
6  Start the Backend Server
   Command: npm start

HELPFUL COMMANDS

- To stop any running server: press Ctrl + C in terminal
- To move back to previous folder: cd ..
- To switch between apps: use cd <folder-name>
- npm stands for Node Package Manager, used to manage dependencies




# Deployment Steps for Project

## Step A – Upload Your Project to GitHub
1. Create a repository in your GitHub account.
2. Open VS Code → open your project folder → open the terminal.
3. Initialize Git in your project:
   git init
4. Link your local project to GitHub:
   git remote add origin <repo-url>
5. Add all files:
   git add .
6. Commit changes:
   git commit -m "Initial commit"
7. Set main branch name:
   git branch -M main
8. Push to GitHub:
   git push -u origin main

## Step B – Point Domain to Your Server (Cloudflare)
1. Go to Cloudflare → DNS settings.
2. Create new A record:
   Name: charan (creates subdomain charan.vjstartup.com)
   IPv4 address: 103.248.208.120
   Proxy Status: OFF
3. Verify DNS with:
   ping charan.vjstartup.com

## Step C – Deploy Project to Server
1. Login to server:
   ssh campus@10.45.8.187
   ssh dev-server
2. Navigate to the project folder (e.g., kp-core).
3. Clone the repo:
   git clone <repo-url>
4. Create Nginx config:
   sudo nano /etc/nginx/sites-available/charan
   (Add server block configuration)
5. Test Nginx config:
   sudo nginx -t
6. Reload Nginx configs:
   sudo systemctl daemon-reload
   sudo systemctl reload nginx

## Step D – Enable Site & Deploy Files
1. Enable the site in Nginx:
   sudo ln -s /etc/nginx/sites-available/charan /etc/nginx/sites-enabled/charan
2. Restart Nginx:
   sudo systemctl restart nginx
3. Copy project files to web root:
   sudo cp -r ~/kp-core/charan /var/www/
4. Restart Nginx again:
   sudo systemctl restart nginx

## Step E – Include in Nginx Main Config (Optional)
If nginx.conf does not already include sites-enabled, add:
   include /etc/nginx/sites-enabled/*;
Edit with:
   sudo nano /etc/nginx/nginx.conf

## Step F – Get SSL Certificate
Secure the site with HTTPS:
   sudo certbot --nginx -d charan.vjstartup.com

## Summary
- GitHub stores your code
- Cloudflare points your domain
- Nginx serves your project
- Certbot secures your project with HTTPS


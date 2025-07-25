# Project_Learnings.docx

To copy the content from git to the vs code or our desktop 
Steps :
1.Initialise the git in vs code in the terminal by opening a new folder where you want to copy.
syntax : git init

2. To add a remote named origin to our repository.
syntax : git remote origin

3.git remote
To check in which origin we are

4.git remote -v
to make it ready for push and pull operations
o/p = fetch and push 

5.  Set the user name and email

git config --global user.name "SAI CHARAN"

git config --global user.email "mailid"

6.git branch -m main -> to change if required

7.git pull origin main  -> to pull data

=====================================================
 Switch to E Drive where the project is located
=====================================================
E:

=====================================================
🟩 WARDEN APP SETUP
=====================================================

🔹 Step 1: Go to warden-app folder
cd "KP SIR PROJECT\hostel-food\warden-app"

🔹 Step 2: Install all dependencies from package.json
WHY? This ensures all required libraries (like React) are available.
npm install

🔹 Step 3: Install cross-env (only once)
WHY? Windows does not support setting env variables directly (e.g., PORT=4000). 
cross-env makes this work on all systems including Windows.
npm install cross-env --save-dev

🔹 Step 4: Open package.json for editing
WHY? We need to modify the "start" script to use cross-env.
notepad package.json

✍️ Inside package.json, find and update:
BEFORE:
     "start": "PORT=4000 react-scripts start"
AFTER:
     "start": "cross-env PORT=4000 react-scripts start"
 Save and close Notepad after editing.

🔹 Step 5: Start the Warden React App
:: WHY? This launches the frontend on http://localhost:4000
npm start

=====================================================
 🟦 STUDENT APP SETUP
 =====================================================

🔹 Step 1: Go to student-app folder
cd "..\student-app"

🔹 Step 2: Install all dependencies
npm install

🔹 Step 3: Install cross-env (only once)
npm install cross-env --save-dev

🔹 Step 4: Open package.json to edit start script
notepad package.json

✍️ Inside package.json, find and update:
BEFORE:
    "start": "PORT=3000 react-scripts start"
 AFTER:
    "start": "cross-env PORT=3000 react-scripts start"
 Save and close Notepad.

🔹 Step 5: Start the Student React App
 WHY? This launches the frontend on http://localhost:3000
 npm start

 =====================================================
🟧 BACKEND SERVER SETUP
 =====================================================

🔹 Step 1: Go to backend folder
cd "..\backend"

🔹 Step 2: Install backend dependencies
 WHY? This installs TypeScript, Express, and all other required packages.
npm install

🔹 Step 3: Fix backend start script if needed
notepad package.json

 ✍️ In package.json "scripts" section, update:
 BEFORE:
     "start": "PORT=6201 ts-node src/index.ts"
 AFTER:
     "start": "cross-env PORT=6201 ts-node src/index.ts"
 Save and close Notepad.

🔹 Step 4: Install cross-env (if not installed yet)
npm install cross-env --save-dev

🔹 Step 5: Start the Backend Server
WHY? This launches the API server on http://localhost:6201
npm start


back track
cd ../student-app

to close the backend should click ctrl + c

In package.json change the start to cross-env infront the actual syntax

npm - node package manager.







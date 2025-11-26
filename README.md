# Staffbee HRMS

A comprehensive Human Resource Management System (HRMS) built with Django and modern web technologies. This system provides employee management, attendance tracking, leave management, payroll, recruitment, performance management, and more.

---

## Table of Contents

- [Prerequisites](#prerequisites)
- [System Requirements](#system-requirements)
- [Step-by-Step Installation Guide](#step-by-step-installation-guide)
  - [1. Install Python](#1-install-python)
  - [2. Install PostgreSQL Database](#2-install-postgresql-database)
  - [3. Install Node.js and npm](#3-install-nodejs-and-npm)
  - [4. Install Git](#4-install-git)
  - [5. Install a Code Editor (Optional but Recommended)](#5-install-a-code-editor-optional-but-recommended)
  - [6. Clone the Repository](#6-clone-the-repository)
  - [7. Set Up Python Virtual Environment](#7-set-up-python-virtual-environment)
  - [8. Install Python Dependencies](#8-install-python-dependencies)
  - [9. Install Frontend Dependencies](#9-install-frontend-dependencies)
  - [10. Set Up PostgreSQL Database](#10-set-up-postgresql-database)
  - [11. Configure Environment Variables](#11-configure-environment-variables)
  - [12. Run Database Migrations](#12-run-database-migrations)
  - [13. Build Frontend Assets](#13-build-frontend-assets)
  - [14. Collect Static Files](#14-collect-static-files)
  - [15. Start the Application & Initialize Database](#15-start-the-application--initialize-database)
- [Common Issues and Troubleshooting](#common-issues-and-troubleshooting)
- [Project Structure](#project-structure)
- [Technology Stack](#technology-stack)
- [Contributing](#contributing)

---

## Prerequisites

Before you begin, you'll need to install several tools and applications on your computer. Don't worry if you have nothing installed - this guide will walk you through everything.

## System Requirements

- **Operating System**: Windows 10/11, macOS 10.15+, or Linux (Ubuntu 20.04+)
- **RAM**: Minimum 4GB (8GB recommended)
- **Storage**: At least 2GB free space
- **Internet Connection**: Required for downloading dependencies

---

## Step-by-Step Installation Guide

### 1. Install Python

**What is Python?**
Python is the programming language that powers Django, the web framework this application is built on.

**Why do we need it?**
The backend of this HRMS system is written in Python, so you need Python installed to run the application.

**Installation Steps:**

#### For Windows:
1. Visit [https://www.python.org/downloads/](https://www.python.org/downloads/)
2. Download Python 3.11 or later (recommended: Python 3.11.x)
3. Run the installer
4. **IMPORTANT**: Check the box "Add Python to PATH" during installation
5. Click "Install Now"

#### For macOS:
```bash
# Install using Homebrew (if you don't have Homebrew, install it first from https://brew.sh)
brew install python@3.11
```

#### For Linux (Ubuntu/Debian):
```bash
sudo apt update
sudo apt install python3.11 python3.11-venv python3-pip
```

**Verify Installation:**
```bash
python --version
# or
python3 --version
```
You should see something like: `Python 3.11.x`

---

### 2. Install PostgreSQL Database

**What is PostgreSQL?**
PostgreSQL is a powerful, open-source relational database system that stores all your application data (employees, attendance records, payroll information, etc.).

**Why do we need it?**
The HRMS application stores all its data in a PostgreSQL database. Without it, the application can't save or retrieve information.

**Installation Steps:**

#### For Windows:
1. Visit [https://www.postgresql.org/download/windows/](https://www.postgresql.org/download/windows/)
2. Download the latest PostgreSQL installer
3. Run the installer
4. During installation:
   - Remember the password you set for the postgres user (you'll need this later)
   - Default port is 5432 (keep this as is)
   - Install pgAdmin (included) for database management

#### For macOS:
```bash
# Using Homebrew
brew install postgresql@15

# Start PostgreSQL service
brew services start postgresql@15
```

#### For Linux (Ubuntu/Debian):
```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

**Verify Installation:**
```bash
psql --version
```
You should see something like: `psql (PostgreSQL) 15.x`

---

### 3. Install Node.js and npm

**What is Node.js and npm?**
Node.js is a JavaScript runtime, and npm (Node Package Manager) helps manage JavaScript libraries. These are used to build and bundle the frontend assets (JavaScript, CSS) of the application.

**Why do we need it?**
This HRMS system uses modern JavaScript libraries (like jQuery, Alpine.js, Select2) for the user interface. npm helps install these libraries, and Laravel Mix (a build tool) bundles them together.

**Installation Steps:**

#### For Windows & macOS:
1. Visit [https://nodejs.org/](https://nodejs.org/)
2. Download the LTS (Long Term Support) version
3. Run the installer
4. Follow the installation wizard (default settings are fine)

#### For Linux (Ubuntu/Debian):
```bash
# Install Node.js 18.x LTS
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
```

**Verify Installation:**
```bash
node --version
npm --version
```
You should see version numbers like: `v18.x.x` and `9.x.x`

---

### 4. Install Git

**What is Git?**
Git is a version control system that helps track changes in code and clone repositories from platforms like GitHub.

**Why do we need it?**
You'll use Git to clone (download) this HRMS project from the repository to your local computer.

**Installation Steps:**

#### For Windows:
1. Visit [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Download and run the installer
3. Use default settings during installation

#### For macOS:
```bash
# Git is usually pre-installed on macOS. If not:
brew install git
```

#### For Linux (Ubuntu/Debian):
```bash
sudo apt update
sudo apt install git
```

**Verify Installation:**
```bash
git --version
```
You should see something like: `git version 2.x.x`

---

### 5. Install a Code Editor (Optional but Recommended)

**What is a Code Editor/IDE?**
An Integrated Development Environment (IDE) or code editor is a tool that makes it easier to view, edit, and manage code.

**Why do we need it?**
While not strictly necessary to run the application, a good code editor makes it much easier to view and modify configuration files, debug issues, and understand the codebase.

 **Visual Studio Code (VS Code)** - Most popular, free
   - Download: [https://code.visualstudio.com/](https://code.visualstudio.com/)
   - Recommended extensions: Python, Pylance, PostgreSQL

---

### 6. Clone the Repository

**What does cloning mean?**
Cloning creates a local copy of the project repository from GitHub (or another Git hosting service) onto your computer.

**Why do we need to do this?**
This downloads all the project files, code, and structure to your local machine so you can run and develop the application.

**Steps:**

1. Open your terminal (Command Prompt on Windows, Terminal on macOS/Linux)

2. Navigate to where you want to store the project:
```bash
# Example: Navigate to Desktop
cd Desktop

# Or create a projects folder
mkdir projects
cd projects
```

3. Clone the repository:
```bash
git clone https://github.com/YOUR_USERNAME/staffbee-hrms.git
```
**Note**: Replace `YOUR_USERNAME/staffbee-hrms.git` with the actual repository URL.

4. Navigate into the project directory:
```bash
cd staffbee-hrms
```

**What just happened?**
Git downloaded all the project files from the remote repository to your computer in a folder called `staffbee-hrms`.

---

### 7. Set Up Python Virtual Environment

**What is a virtual environment?**
A virtual environment is an isolated Python environment that keeps this project's dependencies separate from other Python projects on your computer.

**Why do we need it?**
Different projects may require different versions of the same library. Virtual environments prevent conflicts by isolating each project's dependencies.

**Steps:**

1. Make sure you're in the project directory:
```bash
pwd  # On Unix/macOS/Linux (shows current directory)
cd   # On Windows (shows current directory)
```

2. Create a virtual environment:
```bash
# On Windows
python -m venv venv

# On macOS/Linux
python3 -m venv venv
```

**What just happened?**
Python created a new folder called `venv` that contains an isolated Python installation for this project.

3. Activate the virtual environment:
```bash
# On Windows (Command Prompt)
venv\Scripts\activate

# On Windows (PowerShell)
venv\Scripts\Activate.ps1

# On macOS/Linux
source venv/bin/activate
```

**What just happened?**
Activating the virtual environment tells your terminal to use the Python installation inside the `venv` folder instead of your system's Python. You should see `(venv)` at the beginning of your terminal prompt.

**IMPORTANT**: You need to activate this virtual environment every time you open a new terminal to work on this project.

---

### 8. Install Python Dependencies

**What are dependencies?**
Dependencies are external libraries and packages that this project needs to function (like Django, database drivers, PDF generators, etc.).

**Why do we need to install them?**
The project code uses these libraries to provide functionality like user authentication, database connections, API endpoints, report generation, etc.

**Steps:**

1. Make sure your virtual environment is activated (you should see `(venv)` in your terminal)

2. Install all required Python packages:
```bash
pip install -r requirements.txt
```

**What is requirements.txt?**
It's a file that lists all the Python packages and their versions that this project needs.

**What just happened?**
pip (Python package installer) downloaded and installed dozens of libraries including:
- Django (the web framework)
- psycopg2 (PostgreSQL database driver)
- djangorestframework (for building APIs)
- reportlab, xhtml2pdf (for generating PDFs)
- django-import-export (for Excel imports/exports)
- And many more...

This process may take several minutes depending on your internet speed.

**Verify Installation:**
```bash
python -m django --version
```
You should see: `4.2.23`

---

### 9. Install Frontend Dependencies

**What are frontend dependencies?**
These are JavaScript libraries used in the user interface, like jQuery (for DOM manipulation), Select2 (for enhanced dropdowns), Alpine.js (for reactive components), etc.

**Why do we need to install them?**
The application's frontend features (interactive forms, dynamic dropdowns, date pickers, etc.) rely on these JavaScript libraries.

**Steps:**

1. Install npm packages:
```bash
npm install
```

**What is package.json?**
Similar to requirements.txt for Python, package.json lists all the JavaScript packages this project needs.

**What just happened?**
npm downloaded and installed all frontend libraries into a folder called `node_modules`. These include:
- jQuery (JavaScript library)
- Alpine.js (lightweight reactive framework)
- Select2 (enhanced select boxes)
- Laravel Mix (build tool for bundling assets)
- And others...

This may take a few minutes.

---

#### Understanding npm Warnings (Important - Please Read!)

**Don't Panic!** After running `npm install`, you might see some warning messages. This is completely normal and expected. Here's what you need to know:

**What warnings might you see?**
```
npm warn deprecated stable@0.1.8: Modern JS already guarantees...
npm warn deprecated querystring@0.2.0: The querystring API is considered Legacy...

29 vulnerabilities (6 low, 9 moderate, 10 high, 4 critical)

To address issues that do not require attention, run:
  npm audit fix
```

**Why do these warnings appear?**
- Some JavaScript libraries in this project use older dependencies that have been flagged for updates
- npm is being cautious and alerting you to potential security issues
- Most of these warnings are in **development tools** (build tools like Laravel Mix and Webpack), NOT in your actual application

**Are these warnings dangerous?**
**NO!** Here's why:
- ✅ These warnings affect development tools, not your running application
- ✅ They only matter when you're building assets (running `npm run dev`)
- ✅ They do NOT affect your users or the application in production
- ✅ They do NOT prevent the application from working

**What should you do?**

1. **First**, fix what can be automatically fixed:
```bash
npm audit fix
```

**What just happened?**
npm automatically updated many packages to newer, more secure versions. This typically reduces vulnerabilities from 29 down to just 2-3.

2. **Check the remaining warnings** (optional):
```bash
npm audit
```

You'll likely see 1-2 remaining warnings about `webpack-dev-server`. These are safe to ignore because:
- They only affect the development server (not production)
- They require very specific conditions to be exploited
- Your application and production builds are completely safe

**Bottom Line for Non-Technical Users:**
Think of these warnings like "check engine" lights for development tools, not your application. Your HRMS application is safe and secure. Just run `npm audit fix` once, and you're good to go!

---

### 10. Set Up PostgreSQL Database

**What are we doing here?**
We're creating a new database in PostgreSQL specifically for this HRMS application to store its data.

**Why do we need to do this?**
Django needs a database to store information. We need to create an empty database and a user account that Django will use to access it.

**Steps:**

**Note**: You can run these commands from any terminal - your IDE's integrated terminal (VS Code, PyCharm), system terminal, Command Prompt, or PowerShell. It doesn't matter which one you use!

1. Access PostgreSQL command line:

```bash
# On Windows (if psql is in PATH)
psql -U postgres

# On macOS (Homebrew installation)
psql postgres
# If command not found, try: /opt/homebrew/opt/postgresql@15/bin/psql postgres

# On Linux (Ubuntu/Debian)
sudo -u postgres psql
```

**What is psql?**
psql is PostgreSQL's command-line tool that lets you interact with the database. It's separate from your Python project and works from any terminal.

**For macOS users**: If you get "command not found", PostgreSQL's bin directory isn't in your PATH. Either:
- Use the full path: `/opt/homebrew/opt/postgresql@15/bin/psql postgres`
- Or add to PATH: `echo 'export PATH="/opt/homebrew/opt/postgresql@15/bin:$PATH"' >> ~/.zshrc && source ~/.zshrc`

**For Windows users**: You'll be prompted for the postgres user password (the one you set during PostgreSQL installation).

**For Linux users**: You'll be prompted for sudo password, then you'll be in the PostgreSQL prompt.

2. Create a new database:
```sql
CREATE DATABASE staffbee_main;
```

**What just happened?**
You created an empty database called `staffbee_main` where all HRMS data will be stored.

3. Create a database user:
```sql
CREATE USER staffbee WITH PASSWORD 'staffbee';
```

**What just happened?**
You created a database user account with username `staffbee` and password `staffbee`. Django will use these credentials to connect to the database.

**Note**: In production, use a strong password, not 'staffbee'!

4. Grant privileges to the user:
```sql
GRANT ALL PRIVILEGES ON DATABASE staffbee_main TO staffbee;
```

**What just happened?**
You gave the `staffbee` user full access to the `staffbee_main` database.

5. Grant schema privileges (PostgreSQL 15+):
```sql
\c staffbee_main
GRANT ALL ON SCHEMA public TO staffbee;
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO staffbee;
GRANT ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA public TO staffbee;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL ON TABLES TO staffbee;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL ON SEQUENCES TO staffbee;
```

6. Exit PostgreSQL:
```sql
\q
```

**What just happened?**
You exited the PostgreSQL command line and returned to your regular terminal prompt. Now you can continue with the Python/Django commands.

**Understanding Terminal Prompts:**
- **Regular terminal**: Shows something like `user@computer:~$` or `C:\Users\YourName>` or `(venv)` - this is where you run Python, npm, and Django commands
- **PostgreSQL prompt**: Shows `postgres=#` or `staffbee_main=#` - this is where you run SQL commands
- To switch from PostgreSQL back to regular terminal, use `\q`

---

### 11. Configure Environment Variables

**What are environment variables?**
Environment variables are configuration settings that tell the application how to connect to the database, what secret key to use, what timezone to use, etc.

**Why do we need to configure them?**
Different environments (development, production) need different settings. Environment variables keep sensitive information (like database passwords) separate from the code.

---

**SIMPLE VERSION: If You Followed All Previous Steps Exactly**

If you created your database exactly as shown in Step 10 (database name: `staffbee_main`, username: `staffbee`, password: `staffbee`), you only need to do this:

**Step 1:** Copy the template file to create your `.env` file:

```bash
# On Windows (Command Prompt)
copy .env.dist .env

# On macOS/Linux
cp .env.dist .env
```

**What just happened?**
You created a new file called `.env` that contains all your configuration. This file is already set up with the correct database settings!

**Step 2:** Generate a secure SECRET_KEY:

1. Visit [https://djecrety.ir/](https://djecrety.ir/)
2. Click the page (it generates a key automatically)
3. Copy the generated key (it looks like: `a$7h!2x9@4k...`)

**Step 3:** Open the `.env` file in your code editor (VS Code, PyCharm, etc.) and **ONLY change the SECRET_KEY line**:

Find this line:
```
SECRET_KEY=42su!airf58_d5y7-j4--*$r5bxs72!lwt18cxy7xlg!==svdo
```

Replace it with your generated key:
```
SECRET_KEY=your-newly-generated-key-from-djecrety
```

**That's it! Save the file and you're done.** ✅

All other settings in the `.env` file are already correctly configured:
- ✅ Database name: `staffbee_main`
- ✅ Database user: `staffbee`
- ✅ Database password: `staffbee`
- ✅ Timezone: `America/Chicago` (US Central Time)
- ✅ Debug mode: `True` (for development)

---

**ADVANCED VERSION: If You Used Different Database Settings**

If you created your database with different names/passwords, or want to change the timezone, here's what to modify:

Open `.env` in your code editor and update these specific values:

| Setting | What to Change | Example |
|---------|----------------|---------|
| `SECRET_KEY` | **MUST CHANGE** - Get from https://djecrety.ir/ | `SECRET_KEY=a$7h!2x9@4k...` |
| `DB_NAME` | Change if you used a different database name | `DB_NAME=my_database` |
| `DB_USER` | Change if you created a different username | `DB_USER=myusername` |
| `DB_PASSWORD` | Change if you used a different password | `DB_PASSWORD=mypassword` |
| `TIME_ZONE` | Optional - Change if not in US Central Time | `TIME_ZONE=America/New_York` |

**All other settings can stay as-is for development.**

---

**Understanding Your .env File:**

Your `.env` file should look like this after editing:

```env
DEBUG=True                          # Shows detailed errors (development only)
SECRET_KEY=your-generated-key       # ⚠️ MUST CHANGE THIS
ALLOWED_HOSTS=www.example.com,example.com,*
CSRF_TRUSTED_ORIGINS=
TIME_ZONE=America/Chicago           # Or your timezone

# Database Configuration
DB_ENGINE=django.db.backends.postgresql
DB_NAME=staffbee_main               # ✏️ Change if you used different name
DB_USER=staffbee                    # ✏️ Change if you used different username
DB_PASSWORD=staffbee                # ✏️ Change if you used different password
DB_HOST=localhost
DB_PORT=5432
```

**IMPORTANT Security Notes:**
- ⚠️ Never share or commit the `.env` file to GitHub (it's already in `.gitignore`)
- ⚠️ In production, change `DEBUG=False` and use strong passwords
- ⚠️ The default password `staffbee` is fine for local development but NOT for production

---

### 12. Run Database Migrations

**What are migrations?**
Migrations are like blueprints that tell the database what tables, columns, and relationships to create. They define the database structure (schema).

**Why do we need to run them?**
Right now, your `staffbee_main` database is empty. Migrations will create all the necessary tables for employees, attendance, leave requests, payroll, etc.

**Steps:**

1. Make sure your virtual environment is activated and you're in the project directory

2. Run migrations:
```bash
python manage.py migrate
```

**What is manage.py?**
It's Django's command-line utility for administrative tasks like running migrations, creating users, starting the server, etc.

**What just happened?**
Django read all the migration files in the project and executed SQL commands to create tables like:
- `auth_user` (for user accounts)
- `employee_employee` (for employee records)
- `attendance_attendance` (for attendance tracking)
- `leave_leave` (for leave requests)
- `payroll_payslip` (for payroll)
- And many more...

You should see output like:
```
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying base.0001_initial... OK
  Applying base.0002_initial... OK
  Applying base.0003_rename_horillamailtemplate... OK
  Applying base.0004_add_is_new_employee_to_user... OK
  Applying employee.0001_initial... OK
  ...
```

**IMPORTANT:** Make sure you see `Applying base.0004_add_is_new_employee_to_user... OK` in the output. This migration adds a required field for user accounts. If you don't see this, the signup process in Step 15 will fail.

3. **Verify all migrations were applied successfully:**
```bash
python manage.py showmigrations --list
```

All migrations should have an `[X]` mark next to them (not `[ ]`). If you see any unmarked migrations, run `python manage.py migrate` again.

---

### 13. Build Frontend Assets

**What are frontend assets?**
Frontend assets are JavaScript and CSS files that make the user interface work and look good.

**Why do we need to build them?**
The project uses Laravel Mix to bundle and optimize JavaScript files from `static/src/` into a single file in `static/build/` for better performance.

**Steps:**

1. Build the frontend assets:
```bash
npm run dev
```

**What is npm run dev?**
It's a command defined in `package.json` that runs Laravel Mix to compile and bundle JavaScript files.

**What just happened?**
Laravel Mix used Webpack to:
- Bundle all JavaScript files together
- Process and optimize the code
- Output the result to `static/build/`

You should see output like:
```
Laravel Mix v6.0.49

 Compiled Successfully in 3000ms
                              ,           
 File                          Size      
                              <           $
 /static/build/index.js        500 KB    
                              4           
```

---

### 14. Collect Static Files

**What are static files?**
Static files are CSS, JavaScript, images, and other assets that don't change dynamically (unlike database content).

**Why do we need to collect them?**
Django needs to gather all static files from various apps into a single location so they can be served efficiently by the web server.

**Steps:**

1. Collect static files:
```bash
python manage.py collectstatic --noinput
```

**What just happened?**
Django copied all static files (CSS, JavaScript, images) from different apps into the `static/` directory specified in settings.

You should see output like:
```
120 static files copied to '/path/to/staffbee/static'.
```

---

### 15. Start the Application & Initialize Database

**What are we doing in this step?**
Now that everything is set up, we'll start the application and use the built-in web interface to initialize the database with demo data and create your admin account.

**Why use the web interface instead of command line?**
The Staffbee HRMS includes a user-friendly initialization wizard that automatically loads demo data (sample employees, departments, attendance records, etc.) and guides you through creating your admin account - all through your web browser!

---

#### Part A: Start the Development Server

1. Make sure you're in the project directory with your virtual environment activated (you should see `(venv)` in your terminal)

2. Start the Django development server:
```bash
python manage.py runserver
```

**What just happened?**
Django started a web server on your local machine. You should see output like:
```
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
January 11, 2025 - 12:00:00
Django version 4.2.23, using settings 'staffbee.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

**Keep this terminal window open!** The server needs to keep running.

---

#### Part B: Initialize Database Through Web Interface

3. Open your web browser (Chrome, Firefox, Safari, etc.)

4. Navigate to: **[http://localhost:8000/](http://localhost:8000/)**

**What will happen?**
Since this is the first time running the application and the database is empty, you'll be automatically redirected to the Database Initialization page.

5. You'll see a page asking for an **Access Code** to initialize the database.

6. **Enter the access code:** `d3f6a1b2c3d4e5f6a7b8c9d0e1f2a3b4c5d6e7f8a9b0c1d`

   **Where did this code come from?**
   This is the `DB_INIT_PASSWORD` value from your `.env` file. It's a security measure to prevent unauthorized database initialization.

7. Click the **"Initialize Database"** or **"Load Demo Data"** button

**What just happened?**
The system is now:
- ✅ Loading demo data into your database
- ✅ Creating sample employees, departments, job positions
- ✅ Loading sample attendance records, leave requests
- ✅ Setting up payroll data, recruitment records, projects
- ✅ Initializing all HRMS modules with realistic demo data

This process may take 30-60 seconds. **Please wait** for it to complete.

---

#### Part C: Create Your Admin Account

8. After the demo data loads successfully, you'll be guided to create your admin account.

9. Fill in the account creation form:
   - **First Name**: Your first name
   - **Last Name**: Your last name
   - **Email**: Your email address (you'll use this to log in)
   - **Password**: Choose a strong password
   - **Confirm Password**: Re-enter your password

10. Click **"Create Account"** or **"Sign Up"**

**What just happened?**
The system created your admin account with full access to all HRMS features!

---

#### Part D: Log In and Explore

11. You'll be redirected to the login page

12. Log in using:
    - **Email**: The email you just entered
    - **Password**: The password you just created

13. **Welcome to Staffbee HRMS!** 🎉

**What you'll see:**
- A dashboard with employee statistics, attendance charts, leave requests
- Sample employees with complete profiles
- Demo attendance records, payroll data, recruitment candidates
- All HRMS modules ready to explore and test

---

#### Understanding the Demo Data

Your database now contains realistic demo data including:

**Employees & Organization:**
- Multiple sample employees with complete profiles
- Various departments (HR, IT, Sales, Marketing, etc.)
- Different job positions and roles
- Company information

**HR Operations:**
- Attendance records (clock-ins, clock-outs)
- Leave requests (approved, pending, rejected)
- Employee shifts and work types
- Holidays

**Payroll & Benefits:**
- Salary structures
- Payslips
- Allowances and deductions
- Loan accounts

**Recruitment:**
- Job openings
- Candidate applications
- Interview schedules
- Recruitment pipelines

**Performance & Projects:**
- Performance reviews
- Goals and KPIs
- Project assignments
- Task tracking

**Other Modules:**
- Onboarding workflows
- Offboarding processes
- Asset management
- Helpdesk tickets

**Important Notes:**
- ✅ This is demo data - feel free to modify, delete, or add to it
- ✅ You can reset the database anytime by running `python manage.py flush` and reinitializing
- ✅ For production use, you'll want to remove demo data and add real employee information

---

#### Next Steps

**To stop the server:**
Go back to your terminal and press `CTRL+C`

**To restart the server later:**
1. Open terminal
2. Navigate to project directory: `cd path/to/staffbee-hrms`
3. Activate virtual environment: `source venv/bin/activate` (macOS/Linux) or `venv\Scripts\activate` (Windows)
4. Start server: `python manage.py runserver`
5. Visit: [http://localhost:8000/](http://localhost:8000/)

**Congratulations!** 🎉 Your Staffbee HRMS is fully set up and ready to use!

---

## Common Issues and Troubleshooting

### Issue 1: "python: command not found"
**Solution**: Use `python3` instead of `python` on macOS/Linux
```bash
python3 manage.py runserver
```

### Issue 2: "No module named django"
**Solution**: Make sure your virtual environment is activated. You should see `(venv)` in your terminal prompt.
```bash
# Activate it again
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate      # Windows
```

### Issue 3: "psycopg2" installation fails
**Solution**: Install PostgreSQL development headers
```bash
# On Ubuntu/Debian
sudo apt-get install libpq-dev python3-dev

# On macOS
brew install postgresql
```

### Issue 4: Database connection errors
**Solution**:
- Verify PostgreSQL is running: `sudo systemctl status postgresql` (Linux) or check Services (Windows)
- Check your database credentials in `.env` file
- Verify the database exists: `psql -U postgres -l`

### Issue 5: "Port 8000 is already in use"
**Solution**: Either kill the process using port 8000, or run on a different port
```bash
python manage.py runserver 8001
```

### Issue 6: Static files not loading
**Solution**: Run collectstatic again
```bash
python manage.py collectstatic --noinput
```

### Issue 7: npm install fails
**Solution**: Clear npm cache and try again
```bash
npm cache clean --force
npm install
```

### Issue 8: npm shows security vulnerabilities warnings
**This is normal!** See the detailed explanation in [Step 9: Understanding npm Warnings](#understanding-npm-warnings-important---please-read).

**Quick fix:**
```bash
npm audit fix
```

**What this does**: Automatically updates packages to fix most security warnings. The remaining 1-2 warnings are development-only and safe to ignore.

**Remember**: These warnings don't affect your application's security or functionality. They're just precautionary notices about development build tools.

### Issue 9: "column 'is_new_employee' does not exist" error during signup
**Symptom**: When creating your admin account in Step 15, you get an error: `column "is_new_employee" of relation "auth_user" does not exist`

**Root Cause**: The database migration `0004_add_is_new_employee_to_user` was not applied.

**Solution**:
1. Stop the development server (press `CTRL+C`)
2. Apply the missing migration:
```bash
python manage.py migrate base
```
3. Verify it was applied:
```bash
python manage.py showmigrations base
```
You should see:
```
base
 [X] 0001_initial
 [X] 0002_initial
 [X] 0003_rename_horillamailtemplate_staffbeemailtemplate_and_more
 [X] 0004_add_is_new_employee_to_user
```
4. Restart the server:
```bash
python manage.py runserver
```
5. Try the signup process again

**Prevention**: Always ensure Step 12 is completed successfully and all migrations show `[X]` marks when running `python manage.py showmigrations --list`.

---

## Project Structure

```
staffbee-hrms/

   staffbee/              # Main project settings
      settings.py        # Django settings
      urls.py            # Main URL configuration
      wsgi.py            # WSGI configuration for deployment

   employee/              # Employee management app
   attendance/            # Attendance tracking app
   leave/                 # Leave management app
   payroll/               # Payroll processing app
   recruitment/           # Recruitment & hiring app
   pms/                   # Performance Management System
   onboarding/            # Employee onboarding app
   offboarding/           # Employee offboarding app
   helpdesk/              # IT helpdesk ticketing
   project/               # Project management
   documents/             # Document management
   notifications/         # Notification system
   auth/                  # Authentication
   api/                   # REST API endpoints

   static/                # Static files (CSS, JS, images)
      src/               # Source JavaScript files
      build/             # Compiled/bundled assets

   templates/             # HTML templates
   media/                 # User-uploaded files

   manage.py              # Django management script
   requirements.txt       # Python dependencies
   package.json           # Node.js dependencies
   webpack.mix.js         # Laravel Mix configuration
   .env                   # Environment variables (not in git)
   .env.dist              # Environment template
   .gitignore             # Git ignore rules
   README.md              # This file
```

---

## Technology Stack

### Backend
- **Django 4.2.23**: Python web framework
- **PostgreSQL**: Relational database
- **Django REST Framework**: API development
- **Django Auditlog**: Activity logging
- **APScheduler**: Background task scheduling
- **Gunicorn**: WSGI HTTP server for production

### Frontend
- **Alpine.js**: Lightweight reactive framework
- **jQuery**: JavaScript library
- **Select2**: Enhanced select boxes
- **Ionicons**: Icon library
- **Laravel Mix**: Asset compilation

### Additional Libraries
- **ReportLab & xhtml2pdf**: PDF generation
- **django-import-export**: Excel/CSV import/export
- **Pillow**: Image processing
- **QRCode**: QR code generation
- **geopy**: Geolocation services
- **PyZK**: Biometric device integration

---

## Development Workflow

### Daily Development

1. **Start your day:**
```bash
# Navigate to project
cd path/to/staffbee-hrms

# Activate virtual environment
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate      # Windows

# Start development server
python manage.py runserver
```

2. **Make changes to code** using your IDE

3. **If you modify models**, create and run migrations:
```bash
python manage.py makemigrations
python manage.py migrate
```

4. **If you modify JavaScript**, rebuild assets:
```bash
npm run dev
```

5. **Test your changes** in the browser at http://localhost:8000/

### Creating New Apps

```bash
python manage.py startapp app_name
```

### Database Management

```bash
# Create migrations after model changes
python manage.py makemigrations

# Apply migrations
python manage.py migrate

# Reset database (WARNING: deletes all data)
python manage.py flush

# Create database backup
pg_dump staffbee_main > backup.sql

# Restore database backup
psql staffbee_main < backup.sql
```

### Django Shell

Access Python shell with Django context:
```bash
python manage.py shell
```

Example usage:
```python
from employee.models import Employee
employees = Employee.objects.all()
print(employees.count())
```

---

## Production Deployment

**WARNING**: Do NOT use the development server in production!

For production deployment:

1. Set `DEBUG=False` in `.env`
2. Set proper `ALLOWED_HOSTS` in `.env`
3. Generate a strong `SECRET_KEY`
4. Use a production database (not SQLite)
5. Use Gunicorn or uWSGI instead of `runserver`
6. Serve static files with Nginx or Apache
7. Use HTTPS (SSL/TLS certificates)
8. Set up regular database backups
9. Configure logging and monitoring
10. Use environment variables for all sensitive data

### Quick Production Server Setup

```bash
# Install Gunicorn (already in requirements.txt)
pip install gunicorn

# Run with Gunicorn
gunicorn staffbee.wsgi:application --bind 0.0.0.0:8000
```

For complete production setup, consider using Docker (see `Dockerfile` and `docker-compose.yaml` in the project).

---

## Docker Deployment (Alternative)

If you prefer Docker:

1. Install Docker and Docker Compose
2. Build and run:
```bash
docker-compose up --build
```

See `docker.md` for detailed Docker instructions.

---

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Write or update tests
5. Ensure all tests pass: `python manage.py test`
6. Commit your changes: `git commit -m "Description of changes"`
7. Push to your fork: `git push origin feature-name`
8. Create a Pull Request

---

## Support

For issues, questions, or contributions:
- Create an issue on GitHub
- Check existing documentation
- Review Django documentation: https://docs.djangoproject.com/

---

## License

[Specify your license here]

---

## Acknowledgments

Built with Django and powered by open-source technologies.

---

**Last Updated**: January 2025

**Project Version**: 1.0.0

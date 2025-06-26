# Dev Environment

### 2. **Node.js and npm (for Angular)**

Angular depends on **Node.js** and **npm** for managing packages. You'll need to install these to run the Angular CLI, build your app, and serve it.

* **Install Node.js**:

  ```bash
  sudo apt update
  sudo apt install -y nodejs
  sudo apt install -y npm
  ```

  You can also check the version:

  ```bash
  node -v
  npm -v
  ```

* **Install Angular CLI** globally using npm:

  ```bash
  sudo npm install -g @angular/cli
  ```

### 3. **Python 3 and Pip (for Backend)**

You'll need **Python 3** and **pip** to install and manage backend dependencies.

* **Install Python 3**:

  ```bash
  sudo apt update
  sudo apt install -y python3 python3-pip
  ```

  Verify the installation:

  ```bash
  python3 --version
  pip3 --version
  ```

### 4. **Database (optional but useful for backend)**

For backend development, if you plan to use a database like PostgreSQL or MySQL:

* **MySQL**:

  ```bash
  sudo apt install mysql-server
  ```

### 5. **Code Editors**

A good IDE or text editor is crucial for web development.

* **Visual Studio Code** (VS Code):
  VS Code is lightweight, fast, and has plenty of extensions for both Angular and Python.

  * Install VS Code via:

    ```bash
    sudo apt update
    sudo apt install -y code
    ```

* **Alternatives**: If you're low on resources or prefer something simpler, you can also use **Vim**, **Emacs**, or **Geany**.

### 6. **Python Web Framework (Flask/Django)**

For building your backend API, Python offers some popular web frameworks:

* **Flask** (lightweight):

  ```bash
  pip3 install flask
  ```

* **Django** (full-featured):

  ```bash
  pip3 install django
  ```

### 7. **API Development Tools**

For testing your backend APIs, you'll likely need tools to test HTTP requests.

* **Postman** (via Snap):

  ```bash
  sudo snap install postman
  ```

* **Curl** (if you prefer the terminal):

  ```bash
  sudo apt install curl
  ```

### 8. **Git (Version Control)**

You’ll need **Git** to manage version control for both the frontend and backend.

* **Install Git**:

  ```bash
  sudo apt install git
  ```

* **Configure Git** (set up your name and email):

  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "your-email@example.com"
  ```

### 9. **Nginx or Apache (for serving your app)**

You'll need a web server to deploy your app in production.

* **Nginx** (recommended for performance):

  ```bash
  sudo apt install nginx
  ```

* **Apache** (alternative):

  ```bash
  sudo apt install apache2
  ```
  
### 11. **Additional Tools**

* **Python Virtual Environment** (for isolating dependencies):

  ```bash
  python3 -m venv myenv
  source myenv/bin/activate
  ```

* **Angular Live Reload**:
  Angular's built-in live-reload server can help you see changes in real-time:

  ```bash
  ng serve
  ```

### 12. **Useful Browser Extensions**

* **Angular DevTools**: A Chrome extension to debug and profile Angular apps.
* **Python-specific tools**: Look for extensions that help with syntax highlighting, linting, and auto-formatting (like **Flake8** for Python).

---

### Optional but Useful:

* **Jupyter Notebook** (for Python-based experimentation):

  ```bash
  pip3 install jupyter
  ```

* **PM2** (for process management):
  If you're using Node.js for your backend or frontend services, PM2 can help keep your processes running.

  ```bash
  sudo npm install pm2 -g
  ```

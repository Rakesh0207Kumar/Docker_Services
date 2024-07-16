# Docker_Services

# Clone the Repository:

git clone https://github.com/Rakesh0207Kumar/DockEase.git



# DockEase - Docker Management Application

DockEase is a web-based application for managing Docker images and containers. This README provides instructions to set up and run the application.

## Prerequisites

Before you begin, ensure you have the following installed on your machine:

- Python 3.x
- Docker
- Apache HTTP Server with CGI enabled
- Required Python libraries:
  - `subprocess`
  - `cgi`

## Installation

1. **Install Docker:**

   Follow the official Docker installation guide for your operating system: [Docker Installation](https://docs.docker.com/get-docker/)

2. **Install Apache HTTP Server:**

   **For Ubuntu:**
   ```sh
   sudo apt update
   sudo apt install apache2
   sudo a2enmod cgi
   sudo systemctl restart apache2

  **For CentOS :** 
  ```sh
  sudo yum update
  sudo yum install httpd
  sudo systemctl start httpd
  sudo systemctl enable httpd
  sudo setsebool -P httpd_can_network_connect 1

3. **Setup CGI Script:**

  Create a directory for your CGI scripts if it doesn't already exist and set the correct permissions:
  **Comands**
  ```sh
  sudo mkdir /usr/lib/cgi-bin
  sudo chmod 755 /usr/lib/cgi-bin

Place your Docker.py script in the /usr/lib/cgi-bin/ directory.

4. **Configure Apache to Allow CGI:**

Add the following configuration to your Apache configuration file (e.g., /etc/apache2/sites-available/000-default.conf for Ubuntu or /etc/httpd/conf/httpd.conf for CentOS):
  ```sh
  <Directory "/usr/lib/cgi-bin">
      AllowOverride None
      Options +ExecCGI
      Require all granted
      AddHandler cgi-script .py
  </Directory>

Restart Apache to apply the changes:
  ```sh
  sudo systemctl restart httpd

**Usage**

1. **Place the HTML File:**

Move the index.html file to the appropriate web directory (e.g., /var/www/html/ for Apache):
  ```sh
  cd DockEase
  sudo cp index.html /var/www/html/

2. **Access the Application:**

Open your web browser and navigate to http://<your-server-ip>/index.html to access the DockEase application.

Example Commands
Here are some example commands that you can use within the DockEase application:

Pull Docker Image:
  ```sh
  docker pull <image_name>

Get All Docker Images:
  ```sh
  docker images

Launch a Docker Container:
  ```sh
    docker run -dit <container_name>

Start a Docker Container:
  ```sh
  docker start <container_name>

Stop a Docker Container:
  ```sh
  docker stop <container_name>

Show Running Docker Containers:
  ```sh
  docker ps























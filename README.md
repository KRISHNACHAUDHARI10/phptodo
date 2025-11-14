
# 📝 PHP To-Do List Web Application
A simple and efficient To-Do List web application built using PHP, HTML, CSS, JavaScript, Bootstrap, and MySQL. This application allows users to add, edit, delete, and update tasks with a user-friendly interface.

## 🌟 Features
- Add new tasks 🆕
- Edit existing tasks ✏️
- Mark tasks as completed ✔️
- Delete tasks ❌
- Responsive design using Bootstrap 📱💻

## 🛠️ Technologies Used
- **Frontend**: HTML, CSS, Bootstrap, JavaScript, jQuery
- **Backend**: PHP, MySQL
- **AJAX**: For seamless updates

## 📝 Setup Instructions

Follow these steps to set up the project locally:

### 1. Clone the Repository
```bash
git clone https://github.com/obadaKraishan/ToDoListPHP.git
cd to-do-list
```

### 2. Set Up the Database
1. Start your local server using XAMPP, WAMP, or MAMP.
2. Open phpMyAdmin and create a new database named `todo_list`.
3. Import the SQL file to set up the `tasks` table:
   ```sql
   CREATE DATABASE todo_list;
   USE todo_list;

   CREATE TABLE tasks (
       id INT AUTO_INCREMENT PRIMARY KEY,
       title VARCHAR(255) NOT NULL,
       status ENUM('pending', 'completed') DEFAULT 'pending',
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

### 3. Configure the Database Connection
Edit `includes/db.php` with your database connection details:
```php
<?php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "todo_list";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>
```

### 4. Run the Application
Open a web browser and navigate to `http://localhost/to-do-list`.

## 🎨 Customization
### 1. Update Styles
Modify the styles in `assets/css/styles.css` to match your design preferences.

### 2. Update JavaScript
Enhance the JavaScript functionality in `assets/js/scripts.js` to customize the interactivity.

### 3. Update Content
Modify the HTML content in `index.php` to personalize the text and tasks.

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Contributors
- [Obada Kraishan](https://github.com/obadaKraishan)











🟦 1. Dockerfile

For basic PHP project without frameworks like Laravel:

FROM php:8.2-apache

# Enable Apache mod_rewrite (important for routing)
RUN a2enmod rewrite

# Copy project files to Apache directory
COPY . /var/www/html/

# Set permissions
RUN chown -R www-data:www-data /var/www/html/

EXPOSE 80

🟧 2. .dockerignore
vendor
node_modules
composer.lock
Dockerfile
docker-compose.yml

🟩 3. Build Docker Image

Terminal me project folder se:

docker build -t myphpapp .

🟪 4. Run Container
docker run -p 8080:80 myphpapp


Open browser:

👉 http://localhost:8080

⭐ If PHP project uses MySQL Database, use docker-compose:
🟨 docker-compose.yml
version: '3.8'

services:
  php:
    build: .
    container_name: php_app
    ports:
      - "8080:80"
    volumes:
      - .:/var/www/html
    depends_on:
      - mysql

  mysql:
    image: mysql:5.7
    container_name: mysql_db
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: todo
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql

volumes:
  mysql_data:

⭐ PHP + MySQL Start Command
docker-compose up --build


Your PHP app runs on:

👉 http://localhost:8080

Database runs on:

👉 localhost:3306
User: root
Password: root
DB: todo

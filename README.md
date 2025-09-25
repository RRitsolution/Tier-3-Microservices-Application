🚀 Tier-3 Microservices Based Web Application – PeopleFinder

I recently worked on a 3-Tier Architecture Application to demonstrate how frontend, backend, and database layers interact in a containerized setup.

🏗️ Architecture

Tier-1 (Presentation Layer) → User Interface where users access the application

Tier-2 (Application Logic) → Backend processes requests, connects to DB, and sends results back in required format

Tier-3 (Database Layer) → Stores application data

⚙️ Tech Stack

Frontend → Nginx (HTML, JavaScript)

Backend → Python Flask

Database → MySQL

Deployment → Docker & Docker Compose

🌐 Application Flow

👤 User → 🌍 Browser/Frontend → ⚡ Backend → 🗄️ Database

🔄 How It Works

1️⃣ User hits the frontend URL → Nginx serves HTML and calls backend API (http://localhost:5000/people)
2️⃣ Backend API connects to MySQL, fetches the required data
3️⃣ Database responds → Backend formats response in JSON → Frontend displays data

🛠️ Setup & Execution

Install Git, Docker, Docker-Compose

Clone the repository

Run:

docker compose up -d --build


👉 This starts 3 containers (Frontend, Backend, Database)

Access the frontend at http://localhost:8080

Initially, no people records will be shown (empty DB).

<img width="266" height="103" alt="image" src="https://github.com/user-attachments/assets/ff6f84c0-c4bd-404e-aeb2-783cf6555f46" />


Login to DB container:

docker exec -it <db-container-id> /bin/bash

mysql -u root -p   // It will promt for password pass root

mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| peopledb           |
| performance_schema |
| sys                |
+--------------------+

mysql> USE peopledb;

mysql> SHOW TABLES;
Empty set (0.00 sec)

mysql> CREATE TABLE people (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(10), age INT);

mysql> INSERT INTO people (name,age) VALUES ("jai",35), ("ram",30);
Query OK, 2 rows affected (0.04 sec)
Records: 2  Duplicates: 0  Warnings: 0


mysql> SELECT * FROM people;
+----+------+------+
| id | name | age  |
+----+------+------+
|  1 | jai  |   35 |
|  2 | ram  |   30 |
+----+------+------+
2 rows in set (0.00 sec)


Create table & insert records

Refresh the webpage → People list will be visible 🎉

<img width="273" height="125" alt="image" src="https://github.com/user-attachments/assets/44b86614-acc7-4566-8c08-37ab1e7504f2" />


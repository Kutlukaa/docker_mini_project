# docker_mini_project
Webster Timetable Web Application
This project is a web-based timetable management application designed to display course schedules for different levels in a clear, user-friendly table format. The application retrieves data from a PostgreSQL database and dynamically generates an HTML table to showcase the timetable for the selected level.

Features

Displays a detailed timetable for courses, including course ID, name, day, time, and room.
Responsive and clean design using basic HTML and CSS.
Provides an intuitive interface with links to navigate back to the main page.
Implements dynamic rendering using templating syntax (e.g., Jinja or similar).

Prerequisites
Docker: Used to set up the PostgreSQL database.
PostgreSQL: Database used to store timetable data.
Python (if using Flask/Django for backend logic).
A browser to view the application.


Setup Instructions
1. Database Setup
Run the PostgreSQL container:

bash
docker run --name university-db -e POSTGRES_USER=student -e POSTGRES_PASSWORD=student_pass -d -p 5432:5432 postgres:latest

Connect to the database:
bash
docker exec -it university-db psql -U student


Create the Timetable table:
sql
CREATE TABLE Timetable (
    id SERIAL PRIMARY KEY,
    course_name VARCHAR(255),
    day VARCHAR(50),
    time VARCHAR(50),
    room VARCHAR(255),
    level INT
);
Insert sample data into the table:
sql

INSERT INTO Timetable (course_name, day, time, room, level) VALUES
('Introduction to Cultural Anthropology', 'Thursday', '9:00 AM - 11:20 AM', 'Webster Univ Tashkent', 3),
('Art Appreciation', 'Tuesday', '11:30 AM - 1:50 PM', 'Webster Univ Tashkent', 3),
('Business Spreadsheets', 'Wednesday', '7:00 PM - 8:30 PM', 'Webster Univ Tashkent', 1),
('Introduction to Statistics', 'Wednesday', '7:00 PM - 9:20 PM', 'Webster Univ Tashkent', 1),
('Business Information Systems', 'Friday', '11:30 AM - 1:50 PM', 'Webster Univ Tashkent', 3),
('Computer Languages', 'Wednesday', '4:30 PM - 6:50 PM', 'Webster Univ Tashkent', 2),
('Data Structures I', 'Monday', '2:00 PM - 4:20 PM', 'Webster Univ Tashkent', 2),
('Computer Architecture', 'Friday', '11:30 AM - 1:50 PM', 'Webster Univ Tashkent', 2),
('Survey of Economics', 'Friday', '2:00 PM - 4:20 PM', 'Webster Univ Tashkent', 3),
('Basic Economic Modelling', 'Wednesday', '11:30 AM - 1:50 PM', 'Webster Univ Tashkent', 1);


2. Web Application Setup
Place the HTML file in your project directory.
If using a Python framework like Flask:
Create a route to serve the HTML file dynamically.
Query the PostgreSQL database to fetch timetable data for the selected level.
Pass the data to the HTML template using Jinja (or the templating engine you use).


Usage
Open the application in your browser.
Select a level to view its timetable.
Navigate back to the main page using the provided link.

Project Structure
graphql
project/
├── templates/
│   └── timetable.html   # The main HTML file
├── app.py               # Backend logic (Flask/Django)
├── Dockerfile           # (Optional) Docker configuration for the app

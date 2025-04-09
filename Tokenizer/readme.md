# NanoBlogs

## Table of Contents
1. [Introduction](#introduction)
2. [Project Report](#project-report)
3. [Abstract](#abstract)
4. [Problem Statement](#problem-statement)
5. [System Design](#system-design)
6. [Database Schema](#database-schema)
7. [Application Features](#application-features)
8. [Technologies Used](#technologies-used)
9. [Installation and Setup](#installation-and-setup)
10. [Project Screenshots](#project-screenshots)
11. [Conclusion](#conclusion)

## Introduction
NanoBlogs is a dynamic blogging platform developed using Golang and PostgreSQL, aimed at creating an efficient, scalable, and secure system for content creation and sharing. It enables users to create, read, update, and delete blog posts while offering a smooth and secure experience.

---

## Project Report

### Submitted by:
- Satvik Ahuja (RA2211050010037)  
- Nukul Jain (RA2211050010048)  
- Sunil Kumar (RA2211050010049)

**Under the Guidance of:**  
Dr. Manikandan N, Assistant Professor  
Department of Data Science and Business Systems  
SRM Institute of Science and Technology (SRMIST)  
Kattankulathur - 603203, Tamil Nadu, India  
May 2024

---

## Abstract
NanoBlogs is built as a highly responsive blogging platform leveraging Golang’s speed and concurrency along with PostgreSQL’s robust data handling capabilities. The platform offers features like user authentication, SEO optimization, tagging, content categorization, and real-time interactions through comments and analytics.

### Key Features:
- Efficient and scalable CRUD operations
- User-friendly rich text editor for blog creation
- SEO optimization to increase content visibility
- Responsive design for consistency across devices
- Secure user authentication and access control
- Built-in commenting and engagement system

---

## Problem Statement
The rapidly evolving nature of digital communication calls for a modern, scalable blogging platform that addresses several challenges such as:
- **Performance Bottlenecks:** Sluggish page loads due to inefficient backends
- **Security Issues:** Risks of data breaches and inadequate authentication measures
- **Customization Constraints:** Limited options for tailoring the platform
- **Scalability Concerns:** Inability to handle high user demand and large data volumes

NanoBlogs seeks to address these issues by creating a next-generation platform powered by modern technology.

---

## System Design
The system design focuses on ensuring modularity, maintainability, and scalability. The application is divided into key modules including:
1. **Authentication Module:** Handles user registration and login securely using hashed passwords and JWTs.
2. **Blog Management Module:** Allows users to create, update, delete, and retrieve blogs.
3. **Commenting System:** Supports user comments and interactions.
4. **Database Management:** Efficient storage and retrieval of data using relational schemas.

---

## Database Schema
### Tables:
1. **Users Table:** Stores user credentials and details.
2. **Blogs Table:** Stores blog content, categories, and tags.
3. **Comments Table:** Manages user comments.
4. **Tags Table:** Stores keywords associated with blogs.
5. **Categories Table:** Organizes blogs under specific categories.

```sql
CREATE TABLE Users (
    id UUID PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    username VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    refresh_token VARCHAR(255)
);

CREATE TABLE Blogs (
    id UUID PRIMARY KEY,
    userid UUID REFERENCES Users(id),
    title VARCHAR(255) NOT NULL,
    content TEXT[] NOT NULL,
    category VARCHAR(255) NOT NULL,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);

CREATE TABLE Comments (
    id UUID PRIMARY KEY,
    postid UUID REFERENCES Blogs(id),
    userid UUID REFERENCES Users(id),
    content TEXT NOT NULL,
    created_at TIMESTAMP
);
```

---

## Application Features
- **User Registration and Authentication:** Secure signup and login functionalities.
- **Blog Management:** CRUD operations for blogs with category and tag management.
- **Commenting System:** Allows interaction and engagement on blog posts.
- **Responsive Design:** Mobile-friendly interface for consistent user experience.

---

## Technologies Used
- **Backend:** Golang
- **Database:** PostgreSQL
- **Frontend:** React.js
- **Authentication:** JWT (JSON Web Tokens)
- **ORM/Database Interaction:** pgx (PostgreSQL driver for Go)

---

## Installation and Setup

### Requirements:
- Go (v1.19 or higher)
- PostgreSQL (v13 or higher)
- Node.js and npm/yarn

### Steps:
1. Clone the repository:
   ```bash
   git clone https://github.com/username/nanoblogs.git
   cd nanoblogs
   ```

2. Set up PostgreSQL database:
   ```sql
   CREATE DATABASE nanoblogs;
   ```

3. Run the backend:
   ```bash
   go run main.go
   ```

4. Start the React frontend:
   ```bash
   cd frontend
   npm install
   npm start
   ```

---

## Project Screenshots
### 1. Create Blogs Page
![Create Blogs](Screenshot%202025-02-03%20at%202.24.00%20PM.png)

### 2. Signup Page
![Signup](Screenshot%202025-02-03%20at%202.23.54%20PM.png)

### 3. View Blogs Page
![View Blogs](Screenshot%202025-02-03%20at%202.23.46%20PM.png)

---

## Conclusion
NanoBlogs successfully demonstrates the creation of a modern, scalable CRUD application with robust backend support and an intuitive frontend design. It leverages Golang's performance benefits and PostgreSQL's reliability to create an optimized blogging experience. Developers can use this as a base for further expansion into features like multimedia integration, social sharing, and advanced analytics.

---

### Contributors
- Satvik Ahuja (RA2211050010037)  
- Nukul Jain (RA2211050010048)  
- Sunil Kumar (RA2211050010049)

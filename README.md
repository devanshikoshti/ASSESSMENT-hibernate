# SimpleBlog - Java Web Technologies Assessment

A lightweight, responsive web-based blogging application developed for Blogify Pvt. Ltd. This system implements a clean Model-View-Controller (MVC) pattern alongside core Java enterprise patterns to handle user authentication, session tracking, and full CRUD operations for blog posts.

## Key Modules and Design Patterns
* **MVC Architecture**: Strict separation of concerns (Models handle database logic, Views handle JSP presentation, and Controllers manage HTTP requests via Servlets).
* **Singleton Design Pattern**: Implemented via a central connection manager (DBConnection) to ensure optimized database connection pooling during runtime.
* **DAO Pattern**: Data Access Object (BlogDAO, UserDAO) abstractions to separate low-level data access operations from business components.
* **Session Management**: Secure state tracking via HttpSession to validate user authentication for restricted blog management features.

## Tech Stack and Environment
* **Frontend**: HTML5, Custom Responsive CSS, JavaServer Pages (JSP)
* **Backend**: Java Servlets, JDBC Core API
* **Database**: MySQL (Relational tables for user profiles and blog entries)
* **Server Environment**: Apache Tomcat

## Core Schema Design
The application runs on a two-tier relational structure handling user accounts and linked blog posts:

```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100),
    password VARCHAR(100)
);

CREATE TABLE blogs (
    id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    title VARCHAR(200),
    content TEXT,
    tags VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Core Project Components
* **User Authentication**: Handles registration pipelines and secure session generation upon successful password matching.
* **Content Management**: Complete Create, Read, Update, and Delete actions for blog items mapped to active users.
* **Query Optimization**: Implements pattern-matching search functionality using title and tag lookups, along with chronological date sorting.

## Local Deployment Workflow
1. Ensure a local MySQL database instance is active and configure the connection credentials inside the DBConnection.java profile.
2. Clone this repository directly into your local IDE workspace.
3. Link and configure your Apache Tomcat Server instance within your deployment workspace.
4. Add the application to your runtime server configuration and deploy.
5. Launch your browser and navigate to: http://localhost:8080/SimpleBlog

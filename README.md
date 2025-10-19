# AirBnB Clone Project

## Overview
The project is a real-world simulation of Airbnb booking platform. It involves a deep dive into **full-stack development**, focusing on backend systems, database design, API development, and application security. The goal is to build a **scalable backend system** while mastering complex architetures, workflows, and collaborative team dynamics. The **Tech Stack**  that will be used includes **Django** framework for Backend Development, **PostgreSQL** for database, **GraphQL** for API Query Language, **Docker** for containerization and **Github Actions** for CI/CD.

## Project Goals 
* Master collaborative team workflows using **GitHub**.
* Deepen their understanding of **backend architecture** and **database design** principles.
* Implement advanced **security** measures for **API development**.
* Gain proficiency in designing and managing **CI/CD pipelines** for efficient deployment.
* Strengthen the ability to document and plan complex software projects effectively.

## Team Roles
| Role | Key Responsibility in the Project |
| :--- | :--- |
| **Backend Developer** | Responsible for implementing API endpoints, database schemas, and business logic. |
| **Database Administrator** | Manages database design, indexing, and optimizations. |
| **DevOps Engineer** | Handles deployment, monitoring, and scaling of the backend services. |
| **QA Engineer** | Ensures the backend functionalities are thoroughly tested and meet quality standards. |

## Technology Stack
| Technology | Purpose in the Project | 
| :--- | :--- |
| **Django** | **Backend Framework:** Python framework used to build the core application logic, handle requests, and manage server-side operations for the booking platform. |
| **PostgreSQL** | **Database System:**  Open-source relational database management system chosen for storage. |
| **GraphQL** | **API Query Language:** Used to create an efficient and powerful API. It allows the client to request *exactly* the data it needs, reducing overhead and improving application speed. |
| **Docker** | **Containerization:** Ensures the application and all its dependecies run consistently across all environments (development, testing, CI/CD, production). |
| **Github Actions** | **CI/CD Platform:** Used to set up the automated **Continuous Integration/Continuous Delivery (CI/CD) pipelines** for automated testing, quality checks, and deployment. |

## Database Design
 ### Table: `Users`
 **Purpose:**  Stores user information.
 | Column Name | Data Type | Constraints | Description |
 |---|---|---|---|
 | `user_id` | `INT` | `PRIMARY KEY`, `AUTO_INCREMENT` | Unique user identifier. |
 | `email` | `VARCHAR(100)` | `NOT NULL`, `UNIQUE` | User's email address. |
 | `first_name` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | User's first name. |
 | `last_name` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | User's last name. |
 | `created_at` | `DATETIME` | `DEFAULT CURRENT_TIMESTAMP` | Timestamp of user creation. |
 
 ### Table: `Properties`
 **Purpose:**  Stores details about available accommodations.
 | Column Name | Data Type | Constraints | Description |
 |---|---|---|---|
 | `property_id` | `INT` | `PRIMARY KEY`, `AUTO_INCREMENT` | Unique property identifier. |
 | `host_id` | `VARCHAR(100)` | `NOT NULL`, `UNIQUE` | User id who owns the properties. |
 | `title` | `VARCHAR(100)` | `NOT NULL`, `UNIQUE` | Property name. |
 | `price_per_night` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | property price per night. |
 | `is_available` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | If the property is availbe for accommodation or not. |
 | `created_at` | `DATETIME` | `DEFAULT CURRENT_TIMESTAMP` | Timestamp of property creation. |
 ### Table: `Bookings`
 **Purpose:**  Stores reservation information.
 | Column Name | Data Type | Constraints | Description |
 |---|---|---|---|
 | `booking_id` | `INT` | `PRIMARY KEY`, `AUTO_INCREMENT` | Unique booking identifier. |
 | `user_id` | `VARCHAR(100)` | `NOT NULL`, `UNIQUE` | User id who reserved the booking. |
 | `property_id` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | Property id of the reserved property. |
 | `start_date` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | Start date of the reservation. |
 | `end_date` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | End date of the reservation. |
 | `total_price` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | Total price of the booking. |
 | `created_at` | `DATETIME` | `DEFAULT CURRENT_TIMESTAMP` | Timestamp of booking creation. |
 ### Table: `Reviews`
 **Purpose:**  Stores feedback information given by guests.
 | Column Name | Data Type | Constraints | Description |
 |---|---|---|---|
 | `review_id` | `INT` | `PRIMARY KEY`, `AUTO_INCREMENT` | Unique review identifier. |
 | `booking_id` | `VARCHAR(100)` | `NOT NULL`, `UNIQUE` | Booking id for which reviews is being given. |
 | `reviewer_id` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | User id who giving feedback. |
 | `rating` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | Review's rating. |
 | `comment` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | Reviewer's feedback. |
 | `created_at` | `DATETIME` | `DEFAULT CURRENT_TIMESTAMP` | Timestamp of user creation. |
 ### Table: `Payments`
 **Purpose:**  Stores payment information.
 | Column Name | Data Type | Constraints | Description |
 |---|---|---|---|
 | `payment_id` | `INT` | `PRIMARY KEY`, `AUTO_INCREMENT` | Unique payment identifier. |
 | `booking_id` | `VARCHAR(100)` | `NOT NULL`, `UNIQUE` | Booking id for which to be paid. |
 | `amount` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | The amount to be paid. |
 | `payment_method` | `VARCHAR(50)` | `NOT NULL`, `UNIQUE` | Payment method. |
 | `created_at` | `DATETIME` | `DEFAULT CURRENT_TIMESTAMP` | Timestamp of payment creation. |

### Relationships
 #### Users and Properties (One-to-Many)
   * The `Users` table has a one-to-many relationship with the `Properties` table.
   * `host_id` of `Properties` is a foreign key referencing `user_id` of `Users` table.
 #### Users and Bookings (One-to-Many)
   * The `Users` table has a one-to-many relationship with the `Bookings` table.
   * `user_id` of `Bookings` is a foreign key referencing `user_id` of `Users` table.
 #### Properties and Bookings (One-to-Many)
   * The `Properties` table has a one-to-many relationship with the `Bookings` table.
   * `property_id` of `Bookings` is a foreign key referencing `property_id` of `Properties` table.
 #### Bookings and Reviews (One-to-One/One-to-Many)
   * The `Bookings` table has a one-to-one/One-to-many relationship with the `Reviews` table.
   * `booking_id` of `Reviews` is a foreign key referencing `booking_id` of `Bookings` table.
 #### Bookings and Payments (One-to-One)
   * The `Bookings` table has a one-to-one relationship with the `Payments` table.
   * `booking_id` of `Payments` is a foreign key referencing `booking_id` of `Bookings` table.

### Feature Breakdown
| Feature | Description |
| :--- | :--- |
| **User Management** | This feature handle user management. |
| **Property Management** | This feature handle property management. |
| **Search and Filtering System** | This handle searching and filtering for faster properties findings. |
| **Booking System** | This feature handles reservation related management. |
| **Review and Rating System** | Allows **Guests** to submit feedback and ratings about the experience of thier reservations. |
| **Payment Integration** | Manages the secure initiation and tracking of payment transactions. |

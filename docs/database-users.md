# User Module Database Design

This document describes the database design for user management.

## Tables
1. Roles
2. Users
3. Addresses
------------------------------------------------------------------------------



## Roles

Purpose: Stores different user roles available in the system.

Examples:
- Admin
- Vendor
- Customer

| Column      | Data Type   | Description      |
| ----------- | ----------- | ---------------- |
| role_id     | INT         | Primary Key      |
| role_name   | VARCHAR(50) | Name of role     |
| description | TEXT        | Role description |
| created_at  | DATETIME    | Created time     |

Why do we need this table?

Instead of storing "Admin", "Vendor", or "Customer" inside every user record,
we store them once here.This avoids duplication.
------------------------------------------------------------------------------------------------------------------



## Users

Purpose: Stores all registered users.

| Column            | Type         | Description        |
| ----------------- | ------------ | ------------------ |
| user_id           | BIGINT       | Primary Key        |
| role_id           | INT          | Foreign Key        |
| first_name        | VARCHAR(100) | First Name         |
| last_name         | VARCHAR(100) | Last Name          |
| username          | VARCHAR(50)  | Unique Username    |
| email             | VARCHAR(255) | Login Email        |
| password_hash     | VARCHAR(255) | Encrypted Password |
| phone             | VARCHAR(20)  | Mobile Number      |
| profile_image     | VARCHAR(500) | Image URL          |
| gender            | ENUM         | Gender             |
| date_of_birth     | DATE         | DOB                |
| is_email_verified | BOOLEAN      | Email Status       |
| is_phone_verified | BOOLEAN      | Phone Status       |
| account_status    | ENUM         | Active/Suspended   |
| last_login        | DATETIME     | Last Login         |
| created_at        | DATETIME     | Created            |
| updated_at        | DATETIME     | Updated            |

------------------------------------------------------------------------------------------



### Why password_hash?

Passwords should never be stored as plain text. Instead we store a hashed password.

Example:
Password : hello123
Stored : $2b$12$uF5....

This improves security.
------------------------------------------------------------------------------------------



### Why created_at?

Allows us to know
- when the account was created
- monthly registrations
- analytics
------------------------------------------------------------------------------------------



### Why updated_at?

Allows us to know when user information was modified.
------------------------------------------------------------------------------------------


## Addresses

Purpose: Stores all addresses of users.

| Column        | Type         |
| ------------- | ------------ |
| address_id    | BIGINT       |
| user_id       | BIGINT       |
| full_name     | VARCHAR(150) |
| phone         | VARCHAR(20)  |
| address_line1 | VARCHAR(255) |
| address_line2 | VARCHAR(255) |
| city          | VARCHAR(100) |
| state         | VARCHAR(100) |
| country       | VARCHAR(100) |
| postal_code   | VARCHAR(20)  |
| address_type  | ENUM         |
| is_default    | BOOLEAN      |
| created_at    | DATETIME     |

One user can have multiple addresses.
Example: Home, Office, College

Instead of storing everything inside Users, we separate them.
------------------------------------------------------------------------------------------



Finally draw relationship

Roles
↓
Users
↓
Addresses
------------------------------------------------------------------------------------------



Your file will look like

database-users.md
↓
Introduction
↓
Roles Table
↓
Users Table
↓
Addresses Table
↓
Relationship
↓
Reasons
# Airbnb Database Schema - SQL Definitions

## 📄 Overview

This directory contains the SQL schema file used to define the Airbnb database system for the project. It includes `CREATE TABLE` statements with appropriate constraints, foreign keys, and indexes.

---

## 📁 Files

### `schema.sql`
- Creates six core tables:
  - `users`
  - `properties`
  - `bookings`
  - `payments`
  - `reviews`
  - `messages`
- Includes:
  - Data types and constraints
  - Primary and foreign keys
  - Enum types for specific fields
  - Indexes for optimal query performance

### `README.md`
- Explains the structure and purpose of the SQL script.
- Lists tables and constraints used.

---

## ✅ Constraints and Indexes

- `email` in the `users` table is `UNIQUE`.
- Enum constraints applied for fields like `role`, `status`, and `payment_method`.
- All foreign keys are properly referenced.
- Indexes included on frequently queried columns.

---

## 🔗 Relationships

- A `user` can be a guest, host, or admin.
- A `property` belongs to a `host` (user).
- A `booking` links a `user` to a `property`.
- Each `booking` can have one associated `payment`.
- Users can leave `reviews` for properties.
- Users can send `messages` to one another.

---



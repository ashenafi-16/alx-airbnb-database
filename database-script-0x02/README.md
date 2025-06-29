# Airbnb Database Sample Data

## 📄 Overview

This directory contains SQL scripts for seeding the Airbnb database with sample data for testing and demonstration purposes.

---

## 📁 Files

### `seed.sql`
- Populates the following tables with sample data:
  - `users`
  - `properties`
  - `bookings`
  - `payments`
  - `reviews`
  - `messages`
- The inserted data reflects realistic Airbnb scenarios with multiple users, bookings, and interactions.

---

## 👥 Sample Entities

- **Users**: One guest, one host, one admin.
- **Properties**: Two properties hosted by Bob.
- **Bookings**: Two bookings by Alice.
- **Payments**: One confirmed payment.
- **Reviews**: Alice leaves reviews on both properties.
- **Messages**: Message exchange between Alice and Bob.

---

## 📌 Usage

Run the script after initializing the schema:

```bash
psql -d airbnb_clone -f seed.sql
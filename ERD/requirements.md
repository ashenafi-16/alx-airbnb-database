# Entity-Relationship Diagram Specification

## Objective
Design an Entity-Relationship (ER) diagram for the Airbnb database system based on the specifications provided. This diagram will model the main entities, their attributes, and the relationships between them.

---

## 📦 Entities and Their Attributes

### 1. User
- **user_id** (Primary Key, UUID, Indexed)
- first_name (VARCHAR, NOT NULL)
- last_name (VARCHAR, NOT NULL)
- email (VARCHAR, UNIQUE, NOT NULL)
- password_hash (VARCHAR, NOT NULL)
- phone_number (VARCHAR, NULL)
- role (ENUM: guest, host, admin, NOT NULL)
- created_at (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

### 2. Property
- **property_id** (Primary Key, UUID, Indexed)
- host_id (Foreign Key → User.user_id)
- name (VARCHAR, NOT NULL)
- description (TEXT, NOT NULL)
- location (VARCHAR, NOT NULL)
- pricepernight (DECIMAL, NOT NULL)
- created_at (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)
- updated_at (TIMESTAMP, ON UPDATE CURRENT_TIMESTAMP)

### 3. Booking
- **booking_id** (Primary Key, UUID, Indexed)
- property_id (Foreign Key → Property.property_id)
- user_id (Foreign Key → User.user_id)
- start_date (DATE, NOT NULL)
- end_date (DATE, NOT NULL)
- total_price (DECIMAL, NOT NULL)
- status (ENUM: pending, confirmed, canceled, NOT NULL)
- created_at (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

### 4. Payment
- **payment_id** (Primary Key, UUID, Indexed)
- booking_id (Foreign Key → Booking.booking_id)
- amount (DECIMAL, NOT NULL)
- payment_date (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)
- payment_method (ENUM: credit_card, paypal, stripe, NOT NULL)

### 5. Review
- **review_id** (Primary Key, UUID, Indexed)
- property_id (Foreign Key → Property.property_id)
- user_id (Foreign Key → User.user_id)
- rating (INTEGER, CHECK: rating >= 1 AND rating <= 5, NOT NULL)
- comment (TEXT, NOT NULL)
- created_at (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

### 6. Message
- **message_id** (Primary Key, UUID, Indexed)
- sender_id (Foreign Key → User.user_id)
- recipient_id (Foreign Key → User.user_id)
- message_body (TEXT, NOT NULL)
- sent_at (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

---

## 🔗 Relationships

- **User ↔ Property**: One-to-Many (a host owns many properties)
- **User ↔ Booking**: One-to-Many (a user can make many bookings)
- **Property ↔ Booking**: One-to-Many (a property can have many bookings)
- **Booking ↔ Payment**: One-to-One (each booking has one payment)
- **User ↔ Review**: One-to-Many (a user can write many reviews)
- **Property ↔ Review**: One-to-Many (a property can have many reviews)
- **User ↔ Message (sender/recipient)**: Many-to-Many (via Message table with two foreign keys)

---

## 💡 Notes
- All primary keys are UUIDs and indexed.
- The `email` field in the User table has a unique constraint.
- `rating` values in Review must be between 1 and 5 (inclusive).
- Timestamps are used to track creation and updates for entities.

---


# Database Normalization for Airbnb Database Design

## 🎯 Objective
To ensure the Airbnb database is free from redundancy and update anomalies, we applied normalization techniques up to the **Third Normal Form (3NF)**.

---

## 🧱 Step 1: First Normal Form (1NF)

**Rule**: 
- Eliminate repeating groups
- Ensure each attribute has atomic (indivisible) values
- Each record must be unique

**✅ Already Satisfied In Our Schema**:
- All attributes contain atomic values (e.g., no comma-separated lists or arrays).
- Each table has a clearly defined primary key ensuring uniqueness.

---

## 🔁 Step 2: Second Normal Form (2NF)

**Rule**: 
- Must be in 1NF
- Eliminate partial dependencies (no non-key attribute should depend on part of a composite key)

**✅ Already Satisfied**:
- All primary keys are single-column (UUIDs), not composite.
- All non-key attributes fully depend on the primary key in their respective tables.

---

## 🔗 Step 3: Third Normal Form (3NF)

**Rule**: 
- Must be in 2NF
- Eliminate transitive dependencies (non-key attributes should not depend on other non-key attributes)

**✅ Verified Adjustments**:
We reviewed all tables and confirmed:
- No transitive dependencies exist.
- All non-key fields depend **only on the primary key**.

---

## ✅ Final Verdict

The Airbnb database schema **conforms to 3NF**. Here's a quick justification:

| Table       | Primary Key   | Justification for 3NF |
|-------------|---------------|------------------------|
| User        | user_id       | All attributes describe only the user |
| Property    | property_id   | Attributes depend on property_id only |
| Booking     | booking_id    | Attributes like dates, status, total_price depend only on booking_id |
| Payment     | payment_id    | No derived or dependent fields, clean separation from Booking |
| Review      | review_id     | Rating and comment are directly related to the review |
| Message     | message_id    | No redundancy, sender and recipient are linked via foreign keys |

---

## 💡 Notes

- We avoided derived attributes like `number_of_nights` or `user_full_name` in the schema — these can be calculated at query time or handled in application logic.
- ENUMs are used where appropriate (`status`, `role`, `payment_method`) to enforce domain integrity.

---
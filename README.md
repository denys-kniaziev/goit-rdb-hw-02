# Woolf University. Relational Databases Course. Homework – Database Design: Normalization and ER Modeling

## Overview

This assignment focuses on database normalization and schema design. You will progressively normalize a given table, create an Entity-Relationship (ER) diagram, and implement the final structure in SQL.

---

## Tasks

### 1. Convert to First Normal Form (1NF)

* Ensure that all fields contain **atomic values**.
* Remove repeating groups or arrays.
* Each record must be **uniquely identifiable** by a primary key.

### 2. Convert to Second Normal Form (2NF)

* Eliminate **partial dependencies**.
* Ensure all non-key attributes depend on the **entire primary key**.

### 3. Convert to Third Normal Form (3NF)

* Eliminate **transitive dependencies**.
* Ensure that non-key attributes depend **only** on the primary key.

### 4. Create an ER Diagram

* Model entities, attributes, and relationships.
* Include cardinality (1:1, 1:N, M:N) as appropriate.
* You may use tools like **draw.io**, **Lucidchart**, or **dbdiagram.io**.

### 5. Implement Database Tables

* Use the ER diagram as a blueprint to create SQL `CREATE TABLE` statements.
* Define:

  * Primary keys (`PRIMARY KEY`)
  * Foreign keys (`FOREIGN KEY REFERENCES`)
  * Data types for each column
  * Constraints such as `NOT NULL`, `UNIQUE`, etc.
* Do not insert actual data — structure only.

---

**Deliverables:**

* Normalized table structures (1NF, 2NF, 3NF).
* ER diagram file or image.
* SQL schema with all tables and relationships.

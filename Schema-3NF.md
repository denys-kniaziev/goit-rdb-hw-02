# Third Normal Form (3NF) Database Schema

## Overview
This document describes the database structure after converting to Third Normal Form (3NF). The main goal is to eliminate transitive dependencies by ensuring all non-key attributes depend only on the primary key, not on other non-key attributes.

## What Changed from 2NF?

### Key Transformations:
1. **Separated client information**: Created dedicated `Clients` table
2. **Eliminated transitive dependencies**: Client address no longer depends on client name within orders
3. **Introduced surrogate keys**: Used client IDs for better referential integrity
4. **Created products table**: Separated product information for better data management

## Table Structures

### 1. Clients Table

Stores all client information independently.

| Column Name | Data Type | Description | Constraints |
|-------------|-----------|-------------|-------------|
| Клієнт_ID | INT | Client identifier | PRIMARY KEY, AUTO_INCREMENT |
| Клієнт | VARCHAR(100) | Client name | NOT NULL, UNIQUE |
| Адреса_клієнта | VARCHAR(200) | Client address | NOT NULL |

**Primary Key**: `Клієнт_ID`

### 2. Products Table

Stores all product information.

| Column Name | Data Type | Description | Constraints |
|-------------|-----------|-------------|-------------|
| Товар_ID | INT | Product identifier | PRIMARY KEY, AUTO_INCREMENT |
| Назва_товару | VARCHAR(100) | Product name | NOT NULL, UNIQUE |
| Опис | TEXT | Product description (optional) | NULL |
| Ціна | DECIMAL(10,2) | Product price (optional) | NULL |

**Primary Key**: `Товар_ID`

### 3. Orders Table

Stores order information with reference to clients.

| Column Name | Data Type | Description | Constraints |
|-------------|-----------|-------------|-------------|
| Номер_замовлення | INT | Order number | PRIMARY KEY |
| Клієнт_ID | INT | Client identifier (foreign key) | NOT NULL, FOREIGN KEY |
| Дата_замовлення | DATE | Order date | NOT NULL |

**Primary Key**: `Номер_замовлення`
**Foreign Key**: `Клієнт_ID` REFERENCES `Clients(Клієнт_ID)`

### 4. Order_Items Table

Stores individual products for each order with references to both orders and products.

| Column Name | Data Type | Description | Constraints |
|-------------|-----------|-------------|-------------|
| Замовлення_деталь_ID | INT | Order item identifier | PRIMARY KEY, AUTO_INCREMENT |
| Номер_замовлення | INT | Order number (foreign key) | NOT NULL, FOREIGN KEY |
| Товар_ID | INT | Product identifier (foreign key) | NOT NULL, FOREIGN KEY |
| Кількість | INT | Product quantity | NOT NULL, CHECK (> 0) |

**Primary Key**: `Замовлення_деталь_ID`
**Foreign Keys**: 
- `Номер_замовлення` REFERENCES `Orders(Номер_замовлення)`
- `Товар_ID` REFERENCES `Products(Товар_ID)`
**Unique Constraint**: (`Номер_замовлення`, `Товар_ID`) - prevents duplicate products in same order

## Sample Data

### Clients Table

| Клієнт_ID | Клієнт | Адреса_клієнта |
|-----------|---------|----------------|
| 1 | Мельник | Хрещатик 1 |
| 2 | Шевченко | Басейна 2 |
| 3 | Коваленко | Комп'ютерна 3 |

### Products Table

| Товар_ID | Назва_товару | Опис | Ціна |
|----------|--------------|------|------|
| 1 | Лептоп | Портативний комп'ютер | 25000.00 |
| 2 | Мишка | Комп'ютерна мишка | 350.00 |
| 3 | Принтер | Лазерний принтер | 4500.00 |

### Orders Table

| Номер_замовлення | Клієнт_ID | Дата_замовлення |
|------------------|-----------|-----------------|
| 101 | 1 | 2023-03-15 |
| 102 | 2 | 2023-03-16 |
| 103 | 3 | 2023-03-17 |

### Order_Items Table

| Замовлення_деталь_ID | Номер_замовлення | Товар_ID | Кількість |
|---------------------|------------------|----------|-----------|
| 1 | 101 | 1 | 3 |
| 2 | 101 | 2 | 2 |
| 3 | 102 | 3 | 1 |
| 4 | 103 | 2 | 4 |

## ER Diagram

Refer to: `ER-Diagram-3NF.png`
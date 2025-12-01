# Second Normal Form (2NF) Database Schema

## Overview
This document describes the database structure after converting to Second Normal Form (2NF). The main goal is to eliminate partial dependencies by ensuring all non-key attributes depend on the entire primary key.

## What Changed from 1NF?

### Key Transformations:
1. **Split into multiple tables**: Separated orders and order items
2. **Eliminated partial dependencies**: Non-key attributes now depend on the full primary key
3. **Reduced redundancy**: Order information (date, client, address) stored only once per order

## Table Structures

### 1. Orders Table

Stores main order information with a simple primary key.

| Column Name | Data Type | Description | Constraints |
|-------------|-----------|-------------|-------------|
| Номер_замовлення | INT | Order number | PRIMARY KEY |
| Клієнт | VARCHAR(100) | Client name | NOT NULL |
| Адреса_клієнта | VARCHAR(200) | Client address | NOT NULL |
| Дата_замовлення | DATE | Order date | NOT NULL |

**Primary Key**: `Номер_замовлення`

### 2. Order_Items Table

Stores individual products for each order.

| Column Name | Data Type | Description | Constraints |
|-------------|-----------|-------------|-------------|
| Номер_замовлення | INT | Order number (foreign key) | PRIMARY KEY (part of composite key), FOREIGN KEY |
| Назва_товару | VARCHAR(100) | Product name | PRIMARY KEY (part of composite key) |
| Кількість | INT | Product quantity | NOT NULL, CHECK (> 0) |

**Primary Key**: Composite key of (`Номер_замовлення`, `Назва_товару`)
**Foreign Key**: `Номер_замовлення` REFERENCES `Orders(Номер_замовлення)`

## Sample Data

### Orders Table

| Номер_замовлення | Клієнт | Адреса_клієнта | Дата_замовлення |
|------------------|---------|----------------|-----------------|
| 101 | Мельник | Хрещатик 1 | 2023-03-15 |
| 102 | Шевченко | Басейна 2 | 2023-03-16 |
| 103 | Коваленко | Комп'ютерна 3 | 2023-03-17 |

### Order_Items Table

| Номер_замовлення | Назва_товару | Кількість |
|------------------|--------------|-----------|
| 101 | Лептоп | 3 |
| 101 | Мишка | 2 |
| 102 | Принтер | 1 |
| 103 | Мишка | 4 |

## ER Diagram

Refer to: `ER-Diagram-2NF.png`

## Next Steps

To achieve full normalization and eliminate transitive dependencies:
- **Third Normal Form (3NF)**: Separate client information → [Schema-3NF.md](./Schema-3NF.md)

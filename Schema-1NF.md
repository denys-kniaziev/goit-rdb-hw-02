# First Normal Form (1NF) Database Schema

## Overview
This document describes the database structure after converting to First Normal Form (1NF). The main goal is to eliminate repeating groups and ensure all fields contain atomic (indivisible) values.

## What Changed from Original?

### Key Transformations:
1. **Split non-atomic values**: Separated product names and quantities into individual fields
2. **Eliminated repeating groups**: Each product-order combination now has its own record
3. **Ensured atomicity**: Every field now contains a single, indivisible value

## Table Structure

### Orders Table (1NF)

| Column Name | Data Type | Description | Constraints |
|-------------|-----------|-------------|-------------|
| Номер_замовлення | INT | Order number | PRIMARY KEY (part of composite key) |
| Назва_товару | VARCHAR(100) | Product name | PRIMARY KEY (part of composite key) |
| Кількість | INT | Product quantity | NOT NULL |
| Адреса_клієнта | VARCHAR(200) | Client address | NOT NULL |
| Дата_замовлення | DATE | Order date | NOT NULL |
| Клієнт | VARCHAR(100) | Client name | NOT NULL |

**Primary Key**: Composite key of (`Номер_замовлення`, `Назва_товару`)

## Sample Data

| Номер_замовлення | Назва_товару | Кількість | Адреса_клієнта | Дата_замовлення | Клієнт |
|------------------|--------------|-----------|----------------|-----------------|---------|
| 101 | Лептоп | 3 | Хрещатик 1 | 2023-03-15 | Мельник |
| 101 | Мишка | 2 | Хрещатик 1 | 2023-03-15 | Мельник |
| 102 | Принтер | 1 | Басейна 2 | 2023-03-16 | Шевченко |
| 103 | Мишка | 4 | Комп'ютерна 3 | 2023-03-17 | Коваленко |

## ER Diagram

Refer to: `ER-Diagram-1NF.png`

## Next Steps

To further normalize and eliminate redundancy:
- **Second Normal Form (2NF)**: Remove partial dependencies → [Schema-2NF.md](./Schema-2NF.md)
- **Third Normal Form (3NF)**: Remove transitive dependencies → [Schema-3NF.md](./Schema-3NF.md)

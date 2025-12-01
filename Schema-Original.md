# Original Database Schema (Unnormalized Form)

## Overview
This document describes the original database structure before normalization. The data is stored in a single table with repeating groups and non-atomic values.

## Table Structure

### Orders Table (Original)

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| Номер_замовлення | INT | Order number (identifier) |
| Назва_товару і кількість | TEXT | Product name and quantity (non-atomic) |
| Адреса_клієнта | VARCHAR | Client address |
| Дата_замовлення | DATE | Order date |
| Клієнт | VARCHAR | Client name |

## Sample Data

| Номер_замовлення | Назва_товару і кількість | Адреса_клієнта | Дата_замовлення | Клієнт |
|------------------|--------------------------|----------------|-----------------|---------|
| 101 | Лептоп: 3, Мишка: 2 | Хрещатик 1 | 2023-03-15 | Мельник |
| 102 | Принтер: 1 | Басейна 2 | 2023-03-16 | Шевченко |
| 103 | Мишка: 4 | Комп'ютерна 3 | 2023-03-17 | Коваленко |

## Next Steps

See the following documents for normalized versions:
- [First Normal Form (1NF)](./Schema-1NF.md)
- [Second Normal Form (2NF)](./Schema-2NF.md)
- [Third Normal Form (3NF)](./Schema-3NF.md)

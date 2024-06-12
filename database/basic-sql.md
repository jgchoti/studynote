# Basic SQL

## What is SQL?

SQL stands for Structured Query Language. It is a special-purpose language
used to manage data stored in relational databases. SQL allows users to:

- Interact with existing databases.
- Execute queries to gather insights from the data.
- Define the structure of the data using schemas.

## Relational Databases

Relational databases use tables of data related by common fields (relationships).

- **Tables:** Names should be lowercase, use underscores instead of spaces, and can be collective or plural.
- **Fields:** Columns in a table.
  - Names should be lowercase, without spaces, and singular.
- **Unique Identifier:** A value that distinguishes a record from others in the same table.
- **Schema:** A design blueprint of the database showing tables and their relationships.
- **Row:** Represents a single entity.
- **Column:** Represents an attribute of the entity.

![Relational Databases](https://planetscale.com/_next/image?url=%2Fassets%2Fblog%2Fcontent%2Fschema-design-101-relational-databases%2Fcd0ca647c86b976bd395a8d78fa38b4010ee78d3-1552x872.png&w=1080&q=90)

## MySQL data types

the most commonly used MySQL data types

| Data Type    | Description                                             | Example                    |
|--------------|---------------------------------------------------------|----------------------------|
| INT          | Integer value                                           | `123`, `-456`              |
| VARCHAR      | Variable-length string                                  | `'hello'`, `'example'`     |
| TEXT         | Variable-length text string                             | `'Lorem ipsum...'`         |
| DATE         | Date value                                              | `'2024-06-12'`             |
| TIMESTAMP    | Date and time                                           | `'2024-06-12 10:30:45'`   |
| FLOAT        | Floating-point number                                   | `3.14`, `-0.001`           |
| DOUBLE       | Double-precision floating-point number                  | `123.456`, `-987.654`      |
| BOOLEAN      | Boolean value (0 for false, 1 for true)                 | `0`, `1`                   |
| ENUM         | Enumeration of possible values                           | `'red'`, `'green'`         |
| DECIMAL      | Exact numeric value with decimal precision              | `123.45`, `-9876.543`      |
| CHAR         | Fixed-length character string                           | `'abc'`, `'xyz'`           |
| BLOB         | Binary large object, for storing binary data            | Binary data                |
| JSON         | JSON data type                                          | `{"key": "value"}`         |
| TIME         | Time value                                              | `'10:30:45'`               |



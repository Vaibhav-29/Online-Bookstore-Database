# Online-Bookstore-Database
This project is a simple online bookstore database that allows users to manage books, authors, and customers. It uses the SQLite database management system
-- Create the tables
CREATE TABLE IF NOT EXISTS books (
    book_id INTEGER PRIMARY KEY AUTOINCREMENT,
    title TEXT NOT NULL,
    author_id INTEGER NOT NULL,
    price REAL NOT NULL
);

CREATE TABLE IF NOT EXISTS authors (
    author_id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    email TEXT NOT NULL
);

CREATE TABLE IF NOT EXISTS customers (
    customer_id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    email TEXT NOT NULL
);

-- Insert sample data
INSERT INTO authors (name, email) VALUES
    ('John Smith', 'john@example.com'),
    ('Jane Doe', 'jane@example.com');

INSERT INTO books (title, author_id, price) VALUES
    ('Book 1', 1, 9.99),
    ('Book 2', 1, 14.99),
    ('Book 3', 2, 12.99);

INSERT INTO customers (name, email) VALUES
    ('Alice Johnson', 'alice@example.com'),
    ('Bob Smith', 'bob@example.com');

-- Query to get all books with their authors
SELECT b.title, a.name AS author
FROM books b
JOIN authors a ON b.author_id = a.author_id;

-- Query to get the total number of customers
SELECT COUNT(*) AS total_customers
FROM customers;

-- Query to get the average price of books
SELECT AVG(price) AS average_price
FROM books;

-- Step 1: Create a new database
CREATE DATABASE my_first_db;

-- Step 2: Select the database to use
USE my_first_db;

-- Step 3: Create a sample table for a simple library system
CREATE TABLE books (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    author VARCHAR(100) NOT NULL,
    publication_year INT,
    genre VARCHAR(50),
    price DECIMAL(8,2),
    in_stock BOOLEAN DEFAULT TRUE,
    date_added DATETIME DEFAULT CURRENT_TIMESTAMP
);
' 
-- Step 4: Insert sample data
INSERT INTO books (title, author, publication_year, genre, price) VALUES
('The Great Gatsby', 'F. Scott Fitzgerald', 1925, 'Fiction', 12.99),
('To Kill a Mockingbird', 'Harper Lee', 1960, 'Fiction', 14.50),
('1984', 'George Orwell', 1949, 'Dystopian', 13.25),
('Pride and Prejudice', 'Jane Austen', 1813, 'Romance', 11.75),
('The Catcher in the Rye', 'J.D. Salinger', 1951, 'Fiction', 12.00);

Step 5: Create another table to demonstrate relationships
CREATE TABLE authors (
    author_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    birth_year INT,
    nationality VARCHAR(50)
);

-- Insert author data
INSERT INTO authors (first_name, last_name, birth_year, nationality) VALUES
('F. Scott', 'Fitzgerald', 1896, 'American'),
('Harper', 'Lee', 1926, 'American'),
('George', 'Orwell', 1903, 'British'),
('Jane', 'Austen', 1775, 'British'),
('J.D.', 'Salinger', 1919, 'American');

-- Step 6: Basic queries to explore your data
-- View all books
SELECT * FROM books;

-- View books by genre
SELECT title, author, genre FROM books WHERE genre = 'Fiction';

-- View books published after 1900
SELECT title, author, publication_year FROM books 
WHERE publication_year > 1900 
ORDER BY publication_year;

-- Count books by genre
SELECT genre, COUNT(*) as book_count 
FROM books 
GROUP BY genre;

-- Find books within a price range
SELECT title, author, price FROM books 
WHERE price BETWEEN 12.00 AND 14.00;

-- Update a record
UPDATE books SET price = 15.99 WHERE title = 'The Great Gatsby';

-- Add a new column
ALTER TABLE books ADD COLUMN isbn VARCHAR(13);

-- View table structure
DESCRIBE books;
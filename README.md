#SQL Lab
====

##Getting Started

To get started we'll need to import the booktown.sql file.

1. open terminal - done
2. use the command `psql -f booktown.sql` - done
3. type `sql` to open your psql console - done
4. type \list to ensure the booktown database was successfully completed - done

##Order
1. Find all subjects sorted by subject

Answer: SELECT * FROM subjects ORDER BY subject;
2. Find all subjects sorted by location

Answer: SELECT * FROM subjects ORDER BY location;

##Where
1. Find the book "Little Women"

Answer: SELECT * FROM books WHERE title = 'Little Women';

2. Find all books containing the word "Python"

Answer: SELECT * FROM books WHERE title ILIKE '%Python%'

3. Find all subjects with the location "Main St" sort them by subject

Answer: SELECT * FROM subjects WHERE location = 'Main St' ORDER BY subject

##Joins

1. Find all books about Computers list ONLY book title

Answer: SELECT title FROM books JOIN subjects ON (books.subject_id = subjects.id) WHERE subject_id = '4'

2. Find all books and display ONLY
	* Book title
	* Author's first name
	* Author's last name
	* Book subject

Answer: SELECT title, first_name, last_name, subject FROM books JOIN subjects ON (books.subject_id = subjects.id) JOIN authors ON (books.author_id = authors.id)

3. Find all books that are listed in the stock table
	* Sort them by retail price (most expensive first)
	* Display ONLY: title and price

Answer: SELECT title, retail FROM stock JOIN editions ON (editions.isbn = stock.isbn) JOIN books ON (books.id = editions.book_id) ORDER BY retail ASC

4. Find the book "Dune" and display ONLY
	* Book title
	* ISBN number
	* Publisher name
	* Retail price

Answer: SELECT  title, stock.isbn, retail, name,  FROM stock JOIN editions ON (editions.isbn = stock.isbn) JOIN books ON (books.id = editions.book_id) JOIN publishers ON (editions.publisher_id = publishers.id) WHERE title ILIKE 'dune'

5. Find all shipments sorted by ship date display ONLY:
	* Customer first name
	* Customer last name
	* ship date
	* book title

Answer:SELECT  first_name, last_name, ship_date, title  FROM stock JOIN editions ON (editions.isbn = stock.isbn) JOIN books ON (books.id = editions.book_id) JOIN shipments ON (shipments.isbn = editions.isbn) JOIN customers ON (customers.id = shipments.customer_id) ORDER BY ship_date

# Chinook-Database-Lab-1

Chinook is a sample database available for SQL Server, Oracle, MySQL, etc. It can be created by running a single SQL script.

# Supported Database Servers
- MySQL
- SQL Server
- SQL Server Compact
- SQLite
- PostgreSQL
- Oracle
- DB2

# Data Model
The Chinook data model represents a digital media store, including tables for artists, albums, track, mediatype, playlist, playlisttrack, genre, invoiceline, invoice, customer, and employee.

![alt text](https://video.udacity-data.com/topher/2019/February/5c6164bf_chinook/chinook.png)
# Q1 
The Chinook database contains all invoices from the beginning of 2009 till the end of 2013. The employees at Chinook store are interested in seeing all invoices that happened in 2013 only. Using the Invoice table, write a query that returns all the info of the invoices in 2013.
```sql
SELECT invoice.*
FROM invoice
where invoice.invoicedate between '2013-01-01' and '2014-01-01';
```

# Q2 
The Chinook team decided to run a marketing campaign in Brazil, Canada, india, and Sweden. They will start with the country that has the least customers. Using the customer table, write a query that returns the first name, last name, and country for all customers from the 4 countries.
```sql
SELECT firstName,lastName,country
FROM customer
WHERE country IN("Brazil","Canada","India","Sweden");
```

# Q3
Using the Track and Album tables, write a query that returns all the songs that start with the letter 'A' and the composer field is not empty. Your query should return the name of the song, the name of the composer, and the title of the album.
```sql
SELECT Track.name, Track.Composer, Album.Title 
FROM Track
JOIN Album
ON Track.AlbumId = Album.AlbumId
WHERE Track.name LIKE 'A%' AND Track.Composer NOT LIKE '';
```
# Q4 
The Chinook team would like to throw a promotional Music Festival for their top 10 customers who have spent the most in a single invoice. Write a query that returns the first name, last name, and invoice total for the top 10 invoices ordered by invoice total descending.
```sql
SELECT C.Firstname,C.Lastname,I.Total
FROM Customer AS C
JOIN Invoice AS I
ON C.CustomerId =I.CustomerId
ORDER BY I.total DESC
LIMIT 10

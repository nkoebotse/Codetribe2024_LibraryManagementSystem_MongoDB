
Library Management System - MongoDB Practice Set
Objective
This project aims to create a Library Management System using MongoDB to manage a collection of books, authors, and patrons. The goal is to practice MongoDB CRUD operations, advanced queries, and data manipulation.

Project Requirements:
Database: LibraryDB
Collections:
Books
Authors
Patrons
MongoDB Shell Commands
Below are the specific MongoDB shell commands used to implement the Library Management System, along with brief explanations of each step.

1. Setting Up MongoDB
Starting the MongoDB Shell (Mongosh)
To begin using the MongoDB shell (mongosh), you must have MongoDB installed on your system. If MongoDB is installed correctly, you can start the MongoDB shell by running the following command in your terminal:


mongosh
Once in the shell, you can start interacting with MongoDB by selecting or creating a database.


use LibraryDB
2. Database Creation
Create Database: LibraryDB
In MongoDB, you don’t explicitly create databases. You simply switch to the desired database, and it will be created once you insert data into it.


use LibraryDB
3. Create Collections and Insert Documents
Books Collection
Insert multiple documents into the Books collection using the insertMany() method.


db.books.insertMany([
  { _id: 1, title: "1984", author_id: 1, genres: ["Dystopian", "Political Fiction"], published_year: 1949, available: true },
  { _id: 2, title: "To Kill a Mockingbird", author_id: 2, genres: ["Southern Gothic", "Bildungsroman"], published_year: 1960, available: true },
  { _id: 3, title: "The Great Gatsby", author_id: 3, genres: ["Tragedy"], published_year: 1925, available: true },
  { _id: 4, title: "Brave New World", author_id: 4, genres: ["Dystopian", "Science Fiction"], published_year: 1932, available: true },
  { _id: 5, title: "The Catcher in the Rye", author_id: 5, genres: ["Realist Novel", "Bildungsroman"], published_year: 1951, available: true },
  { _id: 6, title: "Moby-Dick", author_id: 6, genres: ["Adventure Fiction"], published_year: 1851, available: true },
  { _id: 7, title: "Pride and Prejudice", author_id: 7, genres: ["Romantic Novel"], published_year: 1813, available: true },
  { _id: 8, title: "War and Peace", author_id: 8, genres: ["Historical Novel"], published_year: 1869, available: true },
  { _id: 9, title: "Crime and Punishment", author_id: 9, genres: ["Philosophical Novel"], published_year: 1866, available: true },
  { _id: 10, title: "The Hobbit", author_id: 10, genres: ["Fantasy"], published_year: 1937, available: true }
])
Authors Collection
Insert multiple documents into the Authors collection.


db.authors.insertMany([
  { _id: 1, name: "George Orwell", nationality: "British", birth_year: 1903, death_year: 1950 },
  { _id: 2, name: "Harper Lee", nationality: "American", birth_year: 1926, death_year: 2016 },
  { _id: 3, name: "F. Scott Fitzgerald", nationality: "American", birth_year: 1896, death_year: 1940 },
  { _id: 4, name: "Aldous Huxley", nationality: "British", birth_year: 1894, death_year: 1963 },
  { _id: 5, name: "J.D. Salinger", nationality: "American", birth_year: 1919, death_year: 2010 },
  { _id: 6, name: "Herman Melville", nationality: "American", birth_year: 1819, death_year: 1891 },
  { _id: 7, name: "Jane Austen", nationality: "British", birth_year: 1775, death_year: 1817 },
  { _id: 8, name: "Leo Tolstoy", nationality: "Russian", birth_year: 1828, death_year: 1910 },
  { _id: 9, name: "Fyodor Dostoevsky", nationality: "Russian", birth_year: 1821, death_year: 1881 },
  { _id: 10, name: "J.R.R. Tolkien", nationality: "British", birth_year: 1892, death_year: 1973 }
])
Patrons Collection
Insert multiple documents into the Patrons collection.


db.patrons.insertMany([
  { _id: 1, name: "Alice Johnson", email: "alice@example.com", borrowed_books: [] },
  { _id: 2, name: "Bob Smith", email: "bob@example.com", borrowed_books: [1, 2] },
  { _id: 3, name: "Carol White", email: "carol@example.com", borrowed_books: [] },
  { _id: 4, name: "David Brown", email: "david@example.com", borrowed_books: [3] },
  { _id: 5, name: "Eve Davis", email: "eve@example.com", borrowed_books: [] },
  { _id: 6, name: "Frank Moore", email: "frank@example.com", borrowed_books: [4, 5] },
  { _id: 7, name: "Grace Miller", email: "grace@example.com", borrowed_books: [] },
  { _id: 8, name: "Hank Wilson", email: "hank@example.com", borrowed_books: [6] },
  { _id: 9, name: "Ivy Taylor", email: "ivy@example.com", borrowed_books: [] },
  { _id: 10, name: "Jack Anderson", email: "jack@example.com", borrowed_books: [7, 8] }
])
4. CRUD Operations
Read Operations
Find All Books

db.books.find()
Find a Specific Book by Title

db.books.find({ title: "To Kill a Mockingbird" })
Find All Books by a Specific Author

db.books.find({ author_id: 5 })
Find All Available Books

db.books.find({ available: true })
Update Operations
Update Book Availability (Mark as Borrowed)

db.books.updateOne({ _id: 3 }, { $set: { available: false } })
Add a Genre to a Book

db.books.updateOne({ _id: 8 }, { $addToSet: { genres: "Philosophical Fiction" } })
Add a Borrowed Book to a Patron’s Record

db.patrons.updateOne({ _id: 5 }, { $push: { borrowed_books: 8 } })
Delete Operations
Delete a Book by Title


db.books.deleteOne({ title: "Brave New World" })
Delete an Author


db.authors.deleteOne({ _id: 3 })
5. Advanced Queries
Find Books Published After 1950


db.books.find({ published_year: { $gt: 1950 } })
Find All American Authors


db.authors.find({ nationality: "American" })
Set All Books to Available

db.books.updateMany({}, { $set: { available: true } })
Find All Books That Are Available and Published After 1950

db.books.find({ available: true, published_year: { $gt: 1950 } })
Find Authors Whose Names Contain "George" Using $regex

db.authors.find({ name: { $regex: /George/ } })
Increment the Published Year of Books Published in 1869 by 1

db.books.updateMany({ published_year: 1869 }, { $inc: { published_year: 1 } })![4](https://github.com/user-attachments/assets/a623ea33-2d7d-4c37-ba84-dbe366ea17ca)
![3](https://github.com/user-attachments/assets/46a5faee-f04b-450e-80ed-8ac58dd4c5a9)
![2](https://github.com/user-attachments/assets/04c559b3-662c-4640-9539-a06d4005ecdd)
![1](https://github.com/user-attachments/assets/d93ae6b5-126f-49e2-91f3-e71ace225142)

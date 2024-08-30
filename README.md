# Goodreads Clone API

This project is a simple API for managing books and authors, similar to Goodreads.com website .It uses Node.js with Express.js and SQLite for data management.

## Prerequisites

Before you begin, ensure you have met the following requirements:

- Node.js (v16.13.0)
- npm (8.1.0)
- Git

## Project Overview

This project is a simple REST API built with Node.js with Express.js and SQLite to manage books and authors, similar to Goodreads.com website The API allows you to perform CRUD operations on books and retrieve books by authors. It also supports filtering, searching, pagination, and sorting of books.

## Features

- **Get all books**: Retrieve a list of all books.
- **Get a specific book**: Retrieve details of a single book by its ID.
- **Add a new book**: Create a new book entry.
- **Update an existing book**: Update details of a book by its ID.
- **Delete a book**: Delete a book by its ID.
- **Get books by author**: Retrieve a list of books by a specific author.
- **Filter and search books**: Filter and search books with pagination and sorting options.


## Technologies Used

- **Node.js**: A JavaScript runtime built on Chrome's V8 JavaScript engine, used for building scalable and efficient server-side applications.
- **Express.js**: A minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.
- **SQLite**: A self-contained, high-reliability, embedded, full-featured, public-domain SQL database engine used to store data in a local database file.
- **sqlite3**: A Node.js package that provides a straightforward API to interact with the SQLite database using SQL (Structured Query Language) for managing and manipulating relational data.
1. **Install dependencies**:

   ```bash
   npm install
   ```

2. **Install dependencies**:

    ```bash
    npm install express@4.19.2 sqlite@4.2.1 sqlite3@5.1.7 nodemon
    ```

3. **Set up the database**:

    Create an SQLite database (`goodreads.db`) and initialize the tables. You can use a script or create them manually based on the models.



---

## Run the API

1. Navigate to the `Rest-APIS` folder, then to the `myapp` directory.

2. Install the necessary dependencies:

   ```bash
   npm install
   ```

3. Use `nodemon` to automatically restart the server when code changes:

   ```bash
   nodemon index.js
   ```

---

4. **Access the API**:

    The API will be running at `http://localhost:3000`.



5. **Start the server**:

   ```bash
   nodemon index.js
   ```

   The server will start running at `http://localhost:3000/`.


6. **Set up the SQLite database**:

   Ensure you have a SQLite database file named `goodreads.db` in the root directory. You can create the database and the `book` table using the following schema:

   ```sql
   CREATE TABLE book (
     book_id INTEGER PRIMARY KEY AUTOINCREMENT,
     title TEXT NOT NULL,
     author_id INTEGER,
     rating REAL,
     rating_count INTEGER,
     review_count INTEGER,
     description TEXT,
     pages INTEGER,
     date_of_publication TEXT,
     edition_language TEXT,
     price REAL,
     online_stores TEXT
   );
   ```

## API Endpoints

### 1. Get All Books
   - **Endpoint**: `/api/books`
   - **Method**: `GET`
   - **Description**: Retrieves a list of all books.

**Request:**

```http
GET http://localhost:3000/books/
```

**Response:**

```json
[
    {
        "book_id": 1,
        "title": "Harry Potter and the Sorcerers Stone",
        "author_id": 1,
        "rating": 4.48,
        "rating_count": 7464819,
        "review_count": 118312,
        "description": "Harry Potters life is miserable. His parents are dead and hes stuck with his heartless relatives.",
        "pages": 309,
        "date_of_publication": "November 1st 2003",
        "edition_language": "English",
        "price": 750,
        "online_stores": "Amazon, Audible,Google play, Indigo,Abebooks"
    },
    ...
]
```

### 2. Get a Specific Book
   - **Endpoint**: `/api/books/:id`
   - **Method**: `GET`
   - **Description**: Retrieves details of a single book by its ID.

**Request:**

```http
GET http://localhost:3000/books/1/
```

**Response:**

```json
{
    "book_id": 1,
    "title": "Harry Potter and the Sorcerers Stone",
    "author_id": 1,
    "rating": 4.48,
    "rating_count": 7464819,
    "review_count": 118312,
    "description": "Harry Potters life is miserable. His parents are dead and hes stuck with his heartless relatives.",
    "pages": 309,
    "date_of_publication": "November 1st 2003",
    "edition_language": "English",
    "price": 750,
    "online_stores": "Amazon, Audible,Google play, Indigo,Abebooks"
}
```

### 3. Add a New Book
   - **Endpoint**: `/api/books`
   - **Method**: `POST`
   - **Description**: Creates a new book entry.

  **Request:**

```http
POST http://localhost:3000/books/
Content-Type: application/json

{
  "title": "Harry Potter and the Order of the Phoenix",
  "authorId": 1,
  "rating": 4.62,
  "ratingCount": 126559,
  "reviewCount": 611,
  "description": "There is a door at the end of a silent corridor.",
  "pages": 352,
  "dateOfPublication": "May 1st 2003",
  "editionLanguage": "English",
  "price": 850,
  "onlineStores": "Amazon,Audible,Indigo,Apple Books,Google Play,IndieBound"
}
```

**Response:**

```json
{
    "bookId": 43
}
```

### 4. Update an Existing Book
   - **Endpoint**: `/api/books/:id`
   - **Method**: `PUT`
   - **Description**: Updates details of a book by its ID.

  **Request:**

```http
PUT http://localhost:3000/books/41/
Content-Type: application/json

{
  "title": "Harry Potter and the Order of the Phoenix",
  "authorId": 1,
  "rating": 5,
  "ratingCount": 1000000,
  "reviewCount": 711,
  "description": "There is a door at the end of a silent corridor.",
  "pages": 352,
  "dateOfPublication": "May 1st 2003",
  "editionLanguage": "English",
  "price": 850,
  "onlineStores": "Amazon,Audible,Indigo,Apple Books,Google Play,IndieBound"
}
```

**Response:**

```json
{
    "message": "Book Updated Successfully"
}

```
### 5. Delete a Book
   - **Endpoint**: `/api/books/:id`
   - **Method**: `DELETE`
   - **Description**: Deletes a book by its ID.
   
   **Request:**

   ```http
   DELETE http://localhost:3000/books/41/
   ```

   **Response:**

   ```json
   {
      "message": "Book Deleted Successfully"
   }
   ```

### 6. Get Books by Author
   - **Endpoint**: `/api/books/author/:author`
   - **Method**: `GET`
   - **Description**: Retrieves a list of books by a specific author.

**Request:**

```http
GET http://localhost:3000/authors/1/books/
```

**Response:**

```json
[
    {
        "book_id": 1,
        "title": "Harry Potter and the Sorcerers Stone",
        "author_id": 1,
        "rating": 4.48,
        "rating_count": 7464819,
        "review_count": 118312,
        "description": "Harry Potters life is miserable. His parents are dead and hes stuck with his heartless relatives.",
        "pages": 309,
        "date_of_publication": "November 1st 2003",
        "edition_language": "English",
        "price": 750,
        "online_stores": "Amazon, Audible,Google play, Indigo,Abebooks"
    },
    ...
]
```

### 7. Filter and Search Books
   - **Endpoint**: `/api/books/search`
   - **Method**: `GET`
   - **Description**: Filter and search books with pagination and sorting options.
   - **Query Parameters**:
     - `title`: Filter by book title.
     - `author`: Filter by author name.
     - `minPages`: Filter books with at least a certain number of pages.
     - `maxPages`: Filter books with at most a certain number of pages.
     - `publishedAfter`: Filter books published after a specific date.
     - `publishedBefore`: Filter books published before a specific date.
     - `page`: Page number for pagination (default: 1).
     - `limit`: Number of books per page (default: 10).
     - `sortBy`: Sort by a specific field (e.g., `title`, `publishedDate`).
     - `order`: Order of sorting (`asc` for ascending, `desc` for descending).

   **Request:**

```http
GET http://localhost:3000/books/?offset=2&limit=3&search_q=potter&order_by=price&order=DESC
```

**Response:**

```json
[
    {
        "book_id": 1,
        "title": "Harry Potter and the Sorcerers Stone",
        "author_id": 1,
        "rating": 4.48,
        "rating_count": 7464819,
        "review_count": 118312,
        "description": "Harry Potters life is miserable. His parents are dead and hes stuck with his heartless relatives.",
        "pages": 309,
        "date_of_publication": "November 1st 2003",
        "edition_language": "English",
        "price": 750,
        "online_stores": "Amazon, Audible,Google play, Indigo,Abebooks"
    },
    ...
]
```
## Conclusion


This project offers a robust foundation for building a book management system akin to Goodreads. With essential CRUD operations, author-based filtering, and advanced search capabilities, it provides a comprehensive starting point for developers looking to expand into more complex functionalities. The use of Node.js, Express.js, and SQLite ensures a lightweight and efficient system suitable for small to medium-sized applications. Future enhancements could include user authentication, book reviews, and more intricate data relationships, transforming this basic API into a fully-featured book management platform.

---
Published Link: https://goodreads-clone-api-rakesh.onrender.com

---

#### Built By:

Rakesh Pabbathi

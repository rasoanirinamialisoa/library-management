# library-management
API that manages library.
# Library Management API

API for managing a library, providing access to information about books and authors.

## Overview

The Library API allows you to perform various operations related to books and authors, including retrieving books, creating or updating books, and managing authors.

[Explore API in Swagger Petstore Editor](https://petstore.swagger.io/?url=https://raw.githubusercontent.com/rasoanirinamialisoa/library-management/TD1/docs/api.yml)

## Endpoints

### /books

#### GET - Get all books

- Retrieve a list of all books.
- Parameters:
    - `bookName` (optional): Filter books by name.
    - `releaseDateMin` (optional): Filter books with a release date greater than or equal to a specified date.
    - `releaseDateMax` (optional): Filter books with a release date less than or equal to a specified date.
    - `page` (optional): Page number for pagination (default: 1).
    - `sizePage` (optional): Number of items per page (default: 50).
- Responses:
    - 200 - Success: List of filtered books
    - Content Type: application/json
    - Schema: Type: array, Items: [Book](#book)

#### PUT - Create or update a list of books

- Create or update a list of books.
- Request Body: List of books
- Responses:
    - 200 - Success: List of created or updated books
    - Content Type: application/json
    - Schema: Type: array, Items: [Book](#book)

### /books/{bookId}/authors/{authorId}

#### PUT - Modify the author of a book

- Modify the author of a book.
- Parameters:
    - `bookId` (path parameter): ID of the book to be modified.
    - `authorId` (path parameter): ID of the author to be attached to the book.
- Responses:
    - 200 - Author of the book modified successfully
    - Content Type: application/json
    - Schema: [Book](#book)

### /books/authors

#### PUT - Update book authors in bulk

- Update book authors in bulk.
- Request Body: List of objects with bookId and authorId properties.
- Responses:
    - 200 - Authors of the books updated successfully
    - Content Type: application/json
    - Schema: Type: array, Items: [Book](#book)

### /book/{bookId}/topics/{topicId}

#### PUT - Update the topic of a book

- Update the topic of a book by specifying the book ID and the new topic ID.
- Parameters:
  - `bookId` (path parameter): The ID of the book to be updated.
  - `topicId` (path parameter): The ID of the new topic.
- Responses:
  - 200 - Success: Topic of the book updated successfully

### /books/topics

#### PUT - Update the list of available book topics

- Update the list of available book topics.
- Request Body: List of topic identifiers
- Responses:
  - 200 - Success: List of available topics updated successfully


### /authors

#### GET - Get all authors

- Retrieve a list of all authors.
- Parameters:
    - `authorName` (optional): Filter authors by name.
    - `page` (optional): Page number for pagination (default: 1).
    - `pageSize` (optional): Number of items per page (default: 50).
- Responses:
    - 200 - Success: List of filtered authors
    - Content Type: application/json
    - Schema: Type: array, Items: [Author](#author)

#### PUT - Create or update authors

- Create or update authors.
- Request Body: List of authors
- Responses:
    - 200 - Success: Created or updated author
    - Content Type: application/json
    - Schema: Type: array, Items: [Author](#author)

#### DELETE - Delete an author

- Delete an author by ID.
- Parameters:
    - `aId` (path parameter): Author identifier to be deleted.
- Responses:
    - 200 - Success: The author deleted
    - Content Type: application/json
    - Schema: [Author](#author)
### /topics

#### GET - Get all topics

- Retrieve a list of all available topics.
- Responses:
    - 200 - Success: List of topics

#### PUT - Create or update a topic

- Create or update a topic.
- Request Body: Topic information
- Responses:
    - 200 - Success: Created or updated topic

#### DELETE - Delete a topic

- Delete a topic by ID.
- Parameters:
    - `topicId` (path parameter): The ID of the topic to be deleted.
- Responses:
    - 200 - Success: Topic successfully deleted

## Schemas

### Book

- Type: object
- Properties:
    - id (Type: string)
    - bookName (Type: string)
    - author (Reference: [Author](#author))
    - pageNumbers (Type: integer)
    - topic (Type: string, Enum: ROMANCE, COMEDY, OTHER)
    - releaseDate (Type: string, Format: date)

### Author

- Type: object
- Properties:
    - id (Type: string)
    - authorName (Type: string)
    - sex (Type: string, Enum: M, F)

### Sex

- Type: string
- Enum: M, F

### CrupdateBook

- Type: object
- Properties:
    - id (Type: string)
    - bookName (Type: string)
    - pageNumbers (Type: integer)
    - topic (Type: string, Enum: ROMANCE, COMEDY, OTHER)
    - releaseDate (Type: string, Format: date)
### Topic      
- Type: object
  - Properties:
     - topicName, enum (ROMANCE, COMEDY, OTHER)

### UpdateBookAuthor

- Type: object
- Properties:
    - bookId (Type: string)
    - authorId (Type: string)


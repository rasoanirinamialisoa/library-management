# library-management
API that manages library.

## Overview

The Library API provides access to information about books and authors. You can perform operations like retrieving books, creating or updating books, and managing authors.

[Swagger Petstore Editor](https://petstore.swagger.io/?url=https://raw.githubusercontent.com/rasoanirinamialisoa/library-management/TD1/docs/api.yml)

## Endpoints

### /books

#### GET - Get all books

- Retrieve a list of all books.
- Parameters:
    - `bookName` (optional): Filter books by name.
    - `releaseDateStart` (optional): Filter books with a release date greater than or equal to a specified date.
    - `releaseDateEnd` (optional): Filter books with a release date less than or equal to a specified date.
- Responses:
    - 200 - Success: List of filtered books

#### PUT - Create or update a list of books

- Create or update a list of books.
- Request Body: List of books
- Responses:
    - 200 - Success: List of created or updated books

### /authors

#### GET - Get all authors

- Retrieve a list of all authors or filter by name.
- Parameters:
    - `authorName` (optional): Filter authors by name.
- Responses:
    - 200 - Success: List of authors

#### PUT - Create or update an author

- Create or update an author.
- Request Body: Author information
- Responses:
    - 200 - Success: Created or updated author

#### DELETE - Delete an author

- Delete an author by ID.
- Parameters:
    - `authorId` (path parameter): The ID of the author to be deleted.
- Responses:
    - 200 - Success: Author successfully deleted
    - 500 - Internal Server Error

## Schemas

### Book

- Properties: id, bookName, author, pageNumbers, topic, releaseDate

### Author

- Properties: id, name, sex (M or F)
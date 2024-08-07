# SpringBoot-ORM-Relations-RestAPI-QuerysNative-JQPL

This is a Spring Boot application that demonstrates CRUD operations for managing authors, books, users, and numbers (even and odd) with integration to MySQL. The project includes endpoints for various operations and also integrates Swagger for API documentation.

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Project Structure](#project-structure)
- [Endpoints](#endpoints)
- [Usage Examples](#usage-examples)
- [Contribution](#contribution)
- [License](#license)

## Installation

1. Clone the repository:

    ```sh
    git clone https://github.com/Anyel-ec/SpringBoot-ORM-Relations-RestAPI-QuerysNative-JQPL/
    cd SpringBoot-ORM-Relations-RestAPI-QuerysNative-JQPL
    ```

2. Build the project:

    ```sh
    mvn clean install
    ```

3. Run the application:

    ```sh
    mvn spring-boot:run
    ```

## Configuration

Ensure you have MySQL installed and running on your local machine. The default configuration expects MySQL to be running on `localhost:3306` with a database named `app_prueba_numeros`. You can modify the MySQL settings in the `application.properties` file if necessary.

### `application.properties` Example

```properties
spring.application.name=Examen-SpringBoot-U2

# Spring Doc
springdoc.api-docs.enabled=true
springdoc.swagger-ui.enabled=true

# Define the path for swagger-ui
springdoc.swagger-ui.path=/swagger-ui.html

## MYSQL
spring.datasource.url=jdbc:mysql://localhost:3306/app_prueba_numeros
spring.datasource.username=root
spring.datasource.password=anyel
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

## Hibernate Properties
# Hibernate ddl auto (create, create-drop, validate, update)
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=create-drop
```

## Project Structure

```
├── src
│   ├── main
│   │   ├── java
│   │   │   └── top.anyel.appd
│   │   │       ├── controller
│   │   │       │   ├── AuthorsControllerApp.java
│   │   │       │   ├── BooksControllerApp.java
│   │   │       │   ├── DocController.java
│   │   │       │   ├── NumeroControllerApp.java
│   │   │       │   └── UsersControllerApp.java
│   │   │       ├── models
│   │   │       │   ├── AuthorsApp.java
│   │   │       │   ├── BooksApp.java
│   │   │       │   ├── FavoritiesApp.java
│   │   │       │   ├── ImparesApp.java
│   │   │       │   ├── ParesApp.java
│   │   │       │   └── UsersApp.java
│   │   │       ├── repositories
│   │   │       │   └── AuthorsRepositoryApp.java
│   │   │       ├── services
│   │   │       │   ├── AuthorsServiceApp.java
│   │   │       │   ├── BooksServiceApp.java
│   │   │       │   ├── NumeroServiceApp.java
│   │   │       │   └── UsersServiceApp.java
│   │   └── resources
│   │       └── application.properties
│   └── test
│       └── java
│           └── top.anyel.appd
│               └── ExamenSpringBootU2ApplicationTests.java
└── pom.xml
```

## Endpoints

### Authors Management

- `GET /app/authors` - Get all authors
- `GET /app/authors/{id}` - Get an author by ID
- `POST /app/authors` - Create a new author
- `PUT /app/authors/{id}` - Update an existing author
- `DELETE /app/authors/{id}` - Delete an author by ID
- `GET /app/authors/with-books` - Get all authors with their books
- `GET /app/authors/book-author?title={title}` - Get the author of a specific book by title

### Books Management

- `GET /app/books` - Get all books
- `GET /app/books/{id}` - Get a book by ID
- `POST /app/books` - Create a new book
- `PUT /app/books/{id}` - Update an existing book
- `DELETE /app/books/{id}` - Delete a book by ID

### Users Management

- `GET /app/users` - Get all users
- `GET /app/users/{id}` - Get a user by ID
- `POST /app/users` - Create a new user
- `PUT /app/users/{id}` - Update an existing user
- `DELETE /app/users/{id}` - Delete a user by ID
- `GET /app/users/count` - Get the count of all users

### Numbers Management

- `POST /app/numeros/guardar/{numero}` - Save a number
- `GET /app/numeros/tabla/{numero}` - Determine if a number is even or odd
- `GET /app/numeros/pares` - Get all even numbers
- `GET /app/numeros/impares` - Get all odd numbers

### Documentation

- `GET /doc/` - Redirect to Swagger UI

## Usage Examples

### Adding an Author

```json
POST /app/authors
{
  "firstName_ap": "John",
  "lastName_ap": "Doe"
}
```

### Updating a Book

```json
PUT /app/books/1
{
  "title_ap": "New Title",
  "publishingYear_ap": "2021",
  "genre_ap": "Fiction",
  "author_ap": {
    "id_ap": 1
  }
}
```

### Counting Users

```sh
GET /app/users/count
```

## Contribution

If you would like to contribute to this project, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/new-feature`).
3. Make your changes and commit them (`git commit -am 'Add new feature'`).
4. Push your branch (`git push origin feature/new-feature`).
5. Create a Pull Request.

## License

This project is licensed under the ISC License. See the `LICENSE` file for details.

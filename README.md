# 📚 Bookstore Management API

A RESTful API built with Go and MySQL for managing a bookstore's inventory. This project demonstrates clean architecture, CRUD operations, and modern backend development practices.

## 🚀 Features

- **Complete CRUD Operations** - Create, Read, Update, Delete books
- **RESTful Architecture** - Clean and intuitive API endpoints
- **MySQL Integration** - Persistent data storage with GORM ORM
- **JSON API** - Structured request/response handling
- **Modular Design** - Well-organized package structure
- **Auto-Migration** - Database schema management

## 🛠️ Tech Stack

- **Language**: Go (Golang) 1.16
- **Database**: MySQL
- **ORM**: GORM
- **HTTP Router**: Gorilla Mux
- **Data Format**: JSON

## 📋 Prerequisites

Before running this project, make sure you have:

- Go 1.16 or higher installed
- MySQL server running
- Git (for cloning the repository)

## 🔧 Installation & Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/abhinav-phi/bookstore-api.git
   cd bookstore-api
   ```

2. **Install dependencies**
   ```bash
   go mod tidy
   ```

3. **Configure MySQL Database**
   - Create a MySQL database named `bookstore`
   - Update the database connection string in `packages/config/app.go`:
   ```go
   d, err := gorm.Open("mysql", "username:password@tcp(127.0.0.1:3306)/bookstore?charset=utf8&parseTime=True&loc=Local")
   ```

4. **Run the application**
   ```bash
   go run main.go
   ```

The server will start on `http://localhost:9000`

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/book/` | Get all books |
| GET | `/book/{id}` | Get book by ID |
| POST | `/book/` | Create a new book |
| PUT | `/book/{id}` | Update an existing book |
| DELETE | `/book/{id}` | Delete a book |

## 📝 API Usage Examples

### Create a Book
```bash
curl -X POST http://localhost:9000/book/ \
  -H "Content-Type: application/json" \
  -d '{
    "name": "The Go Programming Language",
    "author": "Alan Donovan",
    "publication": "Addison-Wesley"
  }'
```

### Get All Books
```bash
curl -X GET http://localhost:9000/book/
```

### Get Book by ID
```bash
curl -X GET http://localhost:9000/book/1
```

### Update a Book
```bash
curl -X PUT http://localhost:9000/book/1 \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Updated Book Title",
    "author": "Updated Author"
  }'
```

### Delete a Book
```bash
curl -X DELETE http://localhost:9000/book/1
```

## 🏗️ Project Structure

```
bookstore-api/
├── main.go                 # Application entry point
├── go.mod                  # Go module dependencies
├── go.sum                  # Dependency checksums
└── packages/
    ├── config/
    │   └── app.go          # Database configuration
    ├── controllers/
    │   └── book-controller.go  # HTTP handlers
    ├── models/
    │   └── book.go         # Database models
    ├── routes/
    │   └── bookstore-routes.go  # Route definitions
    └── utils/
        └── utils.go        # Utility functions
```

## 📊 Database Schema

The Book model includes:

```go
type Book struct {
    gorm.Model
    Name        string `json:"name"`
    Author      string `json:"author"`
    Publication string `json:"publication"`
}
```

- **ID**: Auto-generated primary key
- **Name**: Book title
- **Author**: Book author
- **Publication**: Publisher name
- **CreatedAt**: Timestamp of creation
- **UpdatedAt**: Timestamp of last update
- **DeletedAt**: Soft delete timestamp

## 🔍 Key Features

### Clean Architecture
- **Separation of Concerns**: Each package has a specific responsibility
- **Dependency Injection**: Database connection managed centrally
- **Error Handling**: Proper error management throughout the application

### Database Integration
- **GORM ORM**: Simplified database operations
- **Auto-Migration**: Automatic schema updates
- **Connection Pooling**: Efficient database connections

### HTTP Handling
- **Gorilla Mux**: Powerful HTTP router
- **JSON Serialization**: Automatic request/response handling
- **RESTful Design**: Standard HTTP methods and status codes

## 🚦 Testing

You can test the API using:
- **Postman**: Import the endpoints and test manually
- **cURL**: Use the command-line examples above
- **Go Tests**: Write unit tests for individual components

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔮 Future Enhancements

- [ ] Authentication and authorization
- [ ] Pagination for book listings
- [ ] Search and filtering capabilities
- [ ] Unit and integration tests
- [ ] Docker containerization
- [ ] API documentation with Swagger
- [ ] Rate limiting
- [ ] Logging middleware

## 📧 Contact

**Abhinav Phi** - [GitHub](https://github.com/abhinav-phi)

Project Link: [https://github.com/abhinav-phi/bookstore-api](https://github.com/abhinav-phi/bookstore-api)

---

⭐ If you found this project helpful, please give it a star!

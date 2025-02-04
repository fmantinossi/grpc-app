﻿# GRPC-APP

This project is a **didactic GRPC application** developed in Go. It serves as an educational tool to explore GRPC concepts and implement a simple streaming service. The application is intended **only for learning purposes** and does not include real-world or commercial use cases.

---

## Features

- **Category Streaming**: GRPC server that provides category information in a streaming format.
- **Evans Integration**: Use Evans, a popular CLI tool, to interact with and test GRPC services.
- **Simple Database**: SQLite is used as a lightweight database to store category and course data.

---

## Project Structure

```
GRPC-APP
├── cmd
│   └── grpcServer
│       └── main.go        # Main entry point for the GRPC server
├── internal
│   ├── database
│   │   ├── category.go    # Category database model and operations
│   │   └── course.go      # Course database model and operations
│   ├── pb
│   │   ├── course_category_grpc.pb.go   # GRPC server and client code (auto-generated)
│   │   └── course_category.pb.go        # Protobuf message code (auto-generated)
│   └── service
│       └── category.go    # GRPC service implementation for category streaming
├── proto
│   └── course_category.proto # Protobuf definition file
├── db.sqlite              # SQLite database file
├── go.mod                 # Go module configuration
├── go.sum                 # Go dependencies
└── README.md              # Project documentation
```

---

## Prerequisites

1. Install [Go](https://go.dev/): Ensure that Go is installed and properly configured on your system.
2. Install [Protocol Buffers Compiler](https://grpc.io/docs/protoc-installation/): Required to generate Go files from `.proto` definitions.
3. Install Evans:
   ```bash
   go install github.com/ktr0731/evans@latest
   ```

---

## Getting Started

### 1. Clone the Repository

```bash
git clone <repository-url>
cd grpc-app
```

### 2. Install Dependencies

Run the following command to install project dependencies:

```bash
go mod tidy
```

### 3. Generate GRPC Code

Ensure `protoc` is installed, then generate the Go files from the `.proto` definition:

```bash
protoc --go_out=. --go-grpc_out=. proto/course_category.proto
```

### 4. Run the GRPC Server

Start the GRPC server with:

```bash
go run cmd/grpcServer/main.go
```

The server will start and listen for incoming GRPC requests.

---

## Testing with Evans

Evans is used to interact with the GRPC services. Follow these steps to test the application:

1. Start Evans:

   ```bash
   evans --host localhost --port 50051 -r
   ```

2. Load the service definition:

   ```
   show service
   ```

3. Interact with the `CategoryService`:

   ```
   call ListCategories
   ```

   The `ListCategories` endpoint streams category data from the server.

---

## Disclaimer

This application is intended solely for educational purposes. It is designed to demonstrate basic GRPC functionality and should not be used in production or as a reference for real-world applications.

---

## Technologies Used

- **Go**: Programming language
- **GRPC**: Remote procedure call framework
- **Protocol Buffers**: Serialization format for defining services and messages
- **SQLite**: Lightweight database
- **Evans**: CLI tool for testing GRPC services

---


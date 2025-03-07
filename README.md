
# Forum API

## Introduction

The **Forum API** is a backend service designed to support a forum platform. It provides user authentication, thread management, comment handling, and reply management functionalities. The project follows a clean architecture approach, ensuring separation of concerns and testability.

---

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Folder Structure](#folder-structure)
- [Dependencies](#dependencies)
- [Testing](#testing)
- [Troubleshooting](#troubleshooting)
- [Contributors](#contributors)
- [License](#license)

---

## Features

- User registration and authentication (login/logout).
- Thread creation and listing.
- Commenting on threads.
- Replies to comments.
- JWT-based authentication.
- PostgreSQL database integration.
- Unit and integration testing.

---

## Installation

1. Clone the repository.
    ```bash
    git clone <repository-url>
    cd forum-api-master
    ```

2. Install dependencies.
    ```bash
    npm install
    ```

3. Set up the database and run migrations.
    - Make sure you have PostgreSQL installed and running.
    - Configure your `.env` file (see [Configuration](#configuration)).

4. Start the server.
    ```bash
    npm start
    ```

5. Run migrations (ensure your database is ready):
    ```bash
    npm run migrate up
    ```

---

## Configuration

Create a `.env` file in the root directory with the following variables:

```
PORT=3000
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_NAME=your_db_name
DB_HOST=localhost
DB_PORT=5432
JWT_SECRET=your_jwt_secret
BCRYPT_SALT_ROUNDS=10
```

---

## Usage

### Starting the Server

```bash
npm start
```

### Available Endpoints

- `POST /users` - Register a new user.
- `POST /authentications` - User login.
- `DELETE /authentications` - User logout.
- `POST /threads` - Create a new thread (requires authentication).
- `GET /threads/{threadId}` - Get details of a thread.
- `POST /threads/{threadId}/comments` - Add comment to a thread.
- `DELETE /threads/{threadId}/comments/{commentId}` - Delete comment.
- And more...

For complete API documentation, refer to the `src/Interfaces/http/api` folder.

---

## Folder Structure

```
src/
├── Applications          # Use cases & business logic
├── Commons                # Shared utilities and error handling
├── Domains                 # Entities & Repositories
├── Infrastructures         # Database, security, server configurations
├── Interfaces              # HTTP Handlers & Routes
└── app.js                   # Entry point
migrations/                  # Database migrations
tests/                       # Test helpers
```

---

## Dependencies

Key dependencies:

- **Hapi.js** - Server framework
- **PostgreSQL** - Database
- **Bcrypt** - Password hashing
- **Jsonwebtoken** - Token management
- **Jest** - Testing framework

For a complete list, check `package.json`.

---

## Testing

Run tests using:

```bash
npm test
```

Tests are organized under:

- `src/**/_test/` for unit tests
- `tests/` for database helpers used in integration tests

---

## Troubleshooting

- **Database Connection Issues**: Ensure your PostgreSQL credentials are correct.
- **Missing Migrations**: Run `npm run migrate up`.
- **JWT Authentication Errors**: Check the `JWT_SECRET` in your `.env`.

---

## Contributors

- [Marfin](https://github.com/marfindev)
- Contributors: Feel free to fork and submit pull requests.

---

## License

This project is licensed under the MIT License.

---

## Notes

This project was built to demonstrate clean architecture in a Node.js project. It can serve as a starting point for larger backend projects.

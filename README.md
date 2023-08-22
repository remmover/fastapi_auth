# Contact Book Web API

Welcome to the Contact Book Web API repository! This repository contains a FastAPI-based web API for managing a contact book. It provides endpoints to create, read, update, and delete contacts, as well as search and retrieve contacts with upcoming birthdays.

## Features

- Create, Read, Update, and Delete (CRUD) operations for contacts.
- Search contacts based on name, surname, or email.
- Retrieve contacts with birthdays in the upcoming week.

## Prerequisites

Before running the API, make sure you have the following installed:

- Python 3.x
- PostgreSQL database

## Getting Started

1. Clone this repository to your local machine.

```bash
git clone https://github.com/remmover/fastapi_app.git
cd contact-book-web-api
```

2. Install the required Python packages using `poetry`:

```bash
poetry install
```

3. Configure the Database URL:

   Open the `src/conf/config.py` file and update the `DB_URL` with your PostgreSQL database connection URL.

4. Run the API:

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

5. Open your web browser and go to `http://localhost:8000/api` to access the API documentation.

## API Endpoints

- **GET /api/contacts**: Get a list of contacts with pagination options.
- **GET /api/contacts/{contact_id}**: Get a single contact by ID.
- **POST /api/contacts**: Create a new contact.
- **PUT /api/contacts/{contact_id}**: Update an existing contact.
- **DELETE /api/contacts/{contact_id}**: Delete a contact.
- **GET /api/contacts/search/{contact_value}**: Search contacts by name, surname, or email.
- **GET /api/contacts/birthday/next-week**: Get contacts with birthdays in the upcoming week.

## Authentication and Authorization

To enhance security and control access to the API, the following mechanisms have been implemented:

- **User Registration**: Users can register with their email and password. Duplicate email registration will result in an HTTP 409 Conflict response.

- **Password Hashing**: The server securely hashes passwords and does not store them in plain text in the database.

- **Authentication**: User authentication for POST operations is done using the user's email and password. An HTTP 401 Unauthorized response is returned if the user does not exist or if the password is incorrect.

- **JWT Token**: JSON Web Tokens (JWT) are used for authorization. Upon successful authentication, the server returns an access token and a refresh token. Users can use the access token to perform authorized operations.

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Feel free to customize the README further with any additional information or details specific to your project. Make sure to replace placeholders like `your-username`, add any additional sections you deem necessary, and include instructions on how to set up and use your web API.

Please implement the authentication mechanism in the application, and also implement the authorization mechanism using JWT tokens to ensure that all contact operations are performed only by registered users. Users should only have access to their own contact operations.

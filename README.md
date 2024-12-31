# Role Based Authorization

This project demonstrates how to implement JWT (JSON Web Token) Authentication in a Node.js API with role-based authorization.

The docker folder contains a docker-compose.yaml file, which sets up MongoDB and MongoDB Express (a web interface for MongoDB) for running and testing the project.


## Getting Started

These instructions will help you set up the project on your local machine for development and testing.

### Prerequisites

Before starting the project, make sure you have the following installed:

Docker
Node.js
MongoDB


### Running the Docker container

Before running the Node JS project, start the Docker containers.

```
docker-compose up -d
```

### Starting the API

Start the Node JS api with the following command from the project's root:

```
npm start
```

## API Routes

### Create User

```
POST /api/users/register
{
    "username": "user",
    "email": "valid@mail.com",
    "password" "the_password"
}
```

### List Users

```
GET /api/users
```

### Assign the User to the "admin" Role

```
POST /api/users/USER_ID/assign-role
{
    "role": "admin"
}
```

### Login (this returns the JWS Token)

```
POST /api/users/login
{
    "email": "valid@mail.com",
    "password" "the_password"
}

RESPONSE
{
    "auth_token": "THE_JWT_TOKEN"
}
```

### Access Authenticated User Information

```
GET /api/users/my-information
HEADERS: {
    "Authorization": "THE_JWT_TOKEN"
}
```


### Access Admin Content

```
GET /api/users/only-admin
HEADERS: {
    "Authorization": "THE_JWT_TOKEN"
}
```


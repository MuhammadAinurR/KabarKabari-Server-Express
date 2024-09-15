## **Server Documentation**

### **Description**

This server is built using Express.js and provides a RESTful API for managing articles and categories. It includes features for authentication, authorization, file uploads, and error handling.

## RESTful endpoints

### Pub Routes

-   [GET /pub/articles](#get-pubarticles) Get all articles
-   [GET /pub/articles/:id](#get-pubarticlesid) Get specified article
-   [GET /pub/categories](#get-pubcategories) Get all categories

### Article Routes

-   [POST /articles](#post-articles) => Create new article
-   [GET /articles](#get-articles) => Get all articles
-   [GET /articles/:id](#get-articlesid) => Get article by id
-   [PUT /articles/:id](#put-articlesid) => Edit article by id
-   [DELETE /articles/:id](#delete-articlesid) => Delete article by id

### Categories Routes

-   [POST /categories](#post-categories) => Create new category
-   [GET /categories](#get-categories) => Get all categories
-   [PUT /categories](#put-categoriesid) => Edit category
-   [DELETE /categories](#delete-categoriesid) => Delete category

### User Routes

-   [POST /register](#user-routes-1) => Create new staff
-   [POST /login](#post-login) => Login

## Pub Routes

### GET /pub/articles

> Get all articles

_Response (200 - OK)_

```json
[
  {
    "id": 3,
    "title": "Pororo",
    "content": "fish and turtle",
    "imgUrl": "this is image url",
    "categoryId": 1,
    "authorId": 2,
    "createdAt": "2024-07-26T01:43:42.060Z",
    "updatedAt": "2024-07-26T01:43:42.060Z",
    "User": {
      "id": 2,
      "username": null,
      "email": "ainurmohstaff@gmail.com",
      "role": "Staff",
      "phoneNumber": null,
      "address": null,
      "createdAt": "2024-07-26T01:43:14.039Z",
      "updatedAt": "2024-07-26T01:43:14.039Z"
    },
    "Category": {
      "id": 1,
      "name": "HotNews",
      "createdAt": "2024-07-26T01:43:14.044Z",
      "updatedAt": "2024-07-26T01:43:14.044Z"
    }
  },
  ...
]
```

---

### GET /pub/articles/:id

> Get article by id

_Response (200 - OK)_

```json
{
    "id": 1,
    "title": "<Article Title>",
    "content": "<Article Title>",
    "imgUrl": "<Article Image URL>",
    "categoryId": "<Article Category ID (INTEGER)>",
    "authorId": "<Article Author/User ID (INTEGER)>",
    "createdAt": "<given date by system>",
    "updatedAt": "<given date by system>"
}
```

_Response (404 - Not Found)_

```json
{
    "message": "Error not found"
}
```

---

### GET /pub/categories

> Get all categories

_Response (200 - OK)_

```json
[
  {
    "id": "<given id by system>",
    "name": "Category Name",
    "createdAt": "given date by system",
    "updatedAt": "given date by system"
  },
    ...
]
```

---

## Articles Routes

| Role  | Create | Read | Update                         | Delete                         |
| ----- | ------ | ---- | ------------------------------ | ------------------------------ |
| Admin | ✅     | ✅   | ✅                             | ✅                             |
| Staff | ✅     | ✅   | Hanya bisa menghapus miliknya. | Hanya bisa menghapus miliknya. |

### POST /articles

> Create new article

_Request Body_

```json
{
    "title": "<article title>",
    "content": "<article content>",
    "imgUrl": "<article image URL>",
    "categoryId": "<articel category id (INTEGER)>"
}
```

_Response (201 - Created)_

```json
{
    "id": "<given id by system>",
    "title": "<article title>",
    "content": "<article content>",
    "imgUrl": "<article image URL>",
    "categoryId": "<articel category id (INTEGER)>",
    "authorId": "<articel author/user id (INTEGER)>",
    "createdAt": "<given date by system>",
    "updatedAt": "<given date by system>"
}
```

_Response (400 - Bad Request)_

```json
{
    "message": "<required attribute> should not empty"
}
```

---

### GET /articles

> Get all articles

_Response (200 - OK)_

```json
[
  {
    "id": 3,
    "title": "Pororo",
    "content": "fish and turtle",
    "imgUrl": "this is image url",
    "categoryId": 1,
    "authorId": 2,
    "createdAt": "2024-07-26T01:43:42.060Z",
    "updatedAt": "2024-07-26T01:43:42.060Z",
    "User": {
      "id": 2,
      "username": null,
      "email": "ainurmohstaff@gmail.com",
      "role": "Staff",
      "phoneNumber": null,
      "address": null,
      "createdAt": "2024-07-26T01:43:14.039Z",
      "updatedAt": "2024-07-26T01:43:14.039Z"
    },
    "Category": {
      "id": 1,
      "name": "HotNews",
      "createdAt": "2024-07-26T01:43:14.044Z",
      "updatedAt": "2024-07-26T01:43:14.044Z"
    }
  },
  ...
]
```

---

### GET /articles/:id

> Get article by id

_Response (200 - OK)_

```json
{
    "id": 1,
    "title": "<Article Title>",
    "content": "<Article Title>",
    "imgUrl": "<Article Image URL>",
    "categoryId": "<Article Category ID (INTEGER)>",
    "authorId": "<Article Author/User ID (INTEGER)>",
    "createdAt": "<given date by system>",
    "updatedAt": "<given date by system>"
}
```

_Response (404 - Not Found)_

```json
{
    "message": "Error not found"
}
```

---

### PUT /articles/:id

> Edit article by id

_Request Body_

```json
{
    "title": "Nea nea",
    "content": "ini adalah cerita tentang nea",
    "imgUrl": "image url",
    "categoryId": 1
}
```

_Response (200 - OK)_

```json
{
    "id": 2,
    "title": "Nea nea",
    "content": "ini adalah cerita tentang nea",
    "imgUrl": "image url",
    "categoryId": 1,
    "authorId": 2,
    "createdAt": "2024-07-26T01:43:37.299Z",
    "updatedAt": "2024-07-26T07:52:02.898Z"
}
```

_Response (404 - Not Found)_

```json
{
    "message": "Error not found"
}
```

_Response (400 - Bad Request)_

```json
{
    "message": ["Title should not empty", "Content should not empty"]
}
```

---

### DELETE /articles/:id

> Delete article by id

_Response (200 - OK)_

```json
{
    "message": "<Article Title> success to delete"
}
```

_Response (404 - Not Found)_

```json
{
    "message": "error not found"
}
```

---

## Categories Routes

### POST /categories

> Create new category

_Request Body_

```json
{
    "name": "<Category Name>"
}
```

_Response (201 - Created)_

```json
{
    "id": "<given id by system>",
    "name": "<Category Name>",
    "createdAt": "given date by system",
    "updatedAt": "given date by system"
}
```

_Response (400 - Bad Request)_

```json
{
    "message": "<empty required attributes>"
}
```

---

### GET /categories

> Get all categories

_Response (200 - OK)_

```json
[
  {
    "id": "<given id by system>",
    "name": "Category Name",
    "createdAt": "given date by system",
    "updatedAt": "given date by system"
  },
    ...
]
```

---

### PUT /categories/:id

> Edit categories by id

_Request Body_

```json
{
    "name": "<new value>"
}
```

_Response (200 - OK)_

```json
{
{
  "id": "<given id by system>",
  "name": "<new value>",
  "createdAt": "<given date by system>",
  "updatedAt": "<given date by system>"
}
}
```

_Response (404 - Not Found)_

```json
{
    "message": "error not found"
}
```

_Response (400 - Bad Request)_

```json
{
    "message": "Validation notEmpty on name failed",
    "type": "Validation error",
    "path": "name",
    "value": "",
    "origin": "FUNCTION",
    "instance": {
        "id": "<Category Id>",
        "name": "",
        "createdAt": "<given date by system>",
        "updatedAt": "<given date by system>"
    },
    "validatorKey": "notEmpty",
    "validatorName": "notEmpty",
    "validatorArgs": [true],
    "original": {
        "validatorName": "notEmpty",
        "validatorArgs": [true]
    }
}
```

---

### DELETE /categories/:id

> Delete categories by id

_Response (200 - OK)_

```json
{
    "message": "<Category Name> success to delete"
}
```

_Response (404 - Not Found)_

```json
{
    "message": "error not found"
}
```

---

## User Routes

### POST /register

> Create new staff

_Request Body_

```json
{
    "email": "asdfasdf@mail.com",
    "password": "nea123456"
}
```

---

_Response (200 - OK)_

```json
{
    "message": {
        "role": "Staff",
        "id": 5,
        "email": "asdfasdf@mail.com",
        "updatedAt": "2024-07-26T09:37:01.994Z",
        "createdAt": "2024-07-26T09:37:01.994Z",
        "username": null,
        "phoneNumber": null,
        "address": null
    }
}
```

---

### POST /login

> Login

_Request Body_

```json
{
    "email": "asdfasdf@mail.com",
    "password": "nea123456"
}
```

---

_Response (200 - OK)_

```json
{
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiaWF0IjoxNzIxOTg2ODIwfQ.vux-8PO6wkV5FHSGaXP7-4uNpOWurtGrfheUgkebuRc",
    "email": "ainurmoh@gmail.com",
    "role": "Admin"
}
```

---

### Global Error

_Response (401 - Unauthorized)_

```json
{
    "message": "Error Authentication"
}
```

---

_Response (403 - Forbidden)_

```json
{
    "message": "Unauthorized Forbidden Error"
}
```

---

_Response (500 - Internal Server Error)_

```json
{
    "message": "Internal Server Error."
}
```

**Middleware**

-   **Authentication Middleware**

    -   **Description**: Verifies the JWT token and attaches the user to the request object.
    -   **Usage**: Applied to routes that require user authentication.

-   **Authorization Middleware**
    -   **Description**: Checks if the user has the necessary permissions to access the route.
    -   **Usage**: Applied to routes that require specific user roles (e.g., admin).

### **Models**

-   **User Model**

    -   **Fields**: `id, email, password, username, phoneNumber, address, role`
    -   **Associations**: `hasMany(Article)`

-   **Article Model**

    -   **Fields**: `id, title, content, imgUrl, categoryId, authorId`
    -   **Associations**: `belongsTo(User), belongsTo(Category)`

-   **Category Model**
    -   **Fields**: `id, name`
    -   **Associations**: `hasMany(Article)`

### **Helpers**

-   **bcrypt.js**

    -   **Description**: Contains functions for hashing passwords and comparing hashed passwords.

-   **jwt.js**

    -   **Description**: Contains functions for signing and verifying JWT tokens.

-   **multer.js**
    -   **Description**: Configures `multer` for handling file uploads and integrates with `cloudinary` for storing images.

### **Deployment**

-   **AWS EC2/GCP**
    -   **Description**: Steps to deploy the server on AWS EC2 or Google Cloud Platform.
    -   **Instructions**: Include setting up the server, configuring environment variables, and deploying the application.

### **Environment Variables**

-   **Description**: List of environment variables required for the application.
-   **Variables**:
    -   `DATABASE_URL`: URL for the database connection.
    -   `JWT_SECRET`: Secret key for signing JWT tokens.
    -   `CLOUDINARY_URL`: URL for Cloudinary configuration.
    -   `PORT`: Port number for the server.

### **Conclusion**

This documentation provides a comprehensive guide to the server's functionality, including authentication, authorization, CRUD operations for articles and categories, file uploads, error handling, and deployment. Follow the instructions and examples provided to effectively use and extend the server's capabilities.

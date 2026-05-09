# API Documentation

Based on the uploaded FastAPI backend code.

---

# Base URL

```txt
https://summedup.onrender.com
```

---

# Authentication

Protected routes require:

```http
Authorization: Bearer <JWT_TOKEN>
```

JWT token is received from:
- `/signup`
- `/login`

---

# APIs

---

## Signup

### Endpoint

```http
GET /signup
```

### Inputs (Query Params)

| Parameter | Type | Required |
|---|---|---|
| email | string | Yes |
| name | string | Yes |
| password | string | Yes |
| phone | string | Yes |

### Example

```http
/signup?email=test@gmail.com&name=John&password=1234&phone=9999999999
```

### Success Response

```json
{
  "access_token": "JWT_TOKEN",
  "token_type": "bearer"
}
```

### Error Responses

```json
{
  "detail": "Email already registered"
}
```

---

## Login

### Endpoint

```http
GET /login
```

### Inputs

| Parameter | Type | Required |
|---|---|---|
| email | string | Yes |
| password | string | Yes |

### Example

```http
/login?email=test@gmail.com&password=1234
```

### Success Response

```json
{
  "access_token": "JWT_TOKEN",
  "token_type": "bearer"
}
```

### Error Response

```json
{
  "detail": "Invalid email or password"
}
```

---

## Profile

### Endpoint

```http
GET /profile
```

### Authentication

Required

### Success Response

```json
{
  "email": "test@gmail.com",
  "name": "John",
  "phone": "9999999999"
}
```

---

## Get Projects

### Endpoint

```http
GET /projects
```

### Authentication

Required

### Success Response

```json
[
  {
    "id": "uuid",
    "name": "Project Name",
    "description": "Project Description"
  }
]
```

---

## Create Project

### Endpoint

```http
GET /create-project
```

### Authentication

Required

### Inputs

| Parameter | Type | Required |
|---|---|---|
| title | string | Yes |
| description | string | Yes |

### Example

```http
/create-project?title=MyProject&description=TestProject
```

### Success Response

```json
{
  "project_id": "uuid"
}
```

---

## Add Stakeholder

### Endpoint

```http
GET /add-stakeholder
```

### Authentication

Required

### Inputs

| Parameter | Type | Required |
|---|---|---|
| project_id | string | Yes |
| email | string | Yes |
| phone | string | Yes |

### Success Response

```json
{
  "message": "Stakeholder added successfully"
}
```

---

## Get Project Stakeholders

### Endpoint

```http
GET /project-stakeholders
```

### Authentication

Required

### Inputs

| Parameter | Type | Required |
|---|---|---|
| project_id | string | Yes |

### Success Response

```json
[
  {
    "id": "uuid",
    "name": "Stakeholder Name",
    "email": "stakeholder@gmail.com",
    "phone": "9999999999"
  }
]
```

---

## Publish Update

### Endpoint

```http
GET /publish-update
```

### Authentication

Required

### Inputs

| Parameter | Type | Required |
|---|---|---|
| project_id | string | Yes |
| title | string | Yes |
| description | string | Yes |

### Success Response

```json
{
  "message": "Update published successfully"
}
```

---

## Get Project Updates

### Endpoint

```http
GET /project-updates
```

### Authentication

Required

### Inputs

| Parameter | Type | Required |
|---|---|---|
| project_id | string | Yes |

### Success Response

```json
[
  {
    "title": "Update Title",
    "description": "Update Description",
    "published_at": "2026-05-10T12:00:00"
  }
]
```

---

## Upload Statement

### Endpoint

```http
GET /upload-statement
```

### Inputs

| Parameter | Type | Required |
|---|---|---|
| update_id | string | Yes |
| message | string | Yes |
| email | string | Yes |

### Success Response

```json
{
  "message": "Statement uploaded successfully"
}
```

---

## Get Update Statements

### Endpoint

```http
GET /update-statements
```

### Authentication

Required

### Inputs

| Parameter | Type | Required |
|---|---|---|
| update_id | string | Yes |

### Success Response

```json
[
  {
    "message": "Statement text",
    "email": "user@gmail.com"
  }
]
```

---



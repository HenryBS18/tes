# API Documentation
All API prefixed with **/api**

## Authentication
- POST /register
- POST /login
- POST /token

---

## POST /register
Register new user.

### Body
```json
{
  "username": "string",
  "password": "string"
}
```

### Success Response (200)
_No response body._

### Error Response (400)
```json
{
  "message": "string"
}
```

---

## POST /login
Login and get token.

### Body
```json
{
  "username": "string",
  "password": "string"
}
```

### Success Response (200)
```json
{
  "token": "string"
}
```

### Error Response (400)
```json
{
  "message": "string"
}
```

---

## POST /token
Validate token.

### Headers
```
Token: <your-token>
```

### Success Response (200)
_No response body._

### Error Response (401)
```json
{
  "message": "string"
}
```

---

## Chat
- GET /chat
- POST /chat/admin
- POST /chat/user
- PATCH /chat/read

---

## GET /chat
Get all chats.

### Success Response (200)
```json
[
  {
    "sessionId": "string",
    "latestChat": {
      "role": "string",
      "message": "string",
      "createdAt": "string"
    },
    "isChatRead": "boolean"
  }
]
```

### Error Response (400)
```json
{
  "message": "string"
}
```

---

## POST /chat/admin
Create new admin chat.

### Headers
```json
Token: <your-token>
```

### Body
```json
{
  "sessionId": "string",
  "message": "string"
}
```

### Success Response (200)
_No response body._

### Error Response (400 | 401)
```json
{
  "message": "string"
}
```

---

## POST /chat/user
Create new user chat.

### Headers
```json
SessionId: <your-sessionid>
```

### Body
```json
{
  "prompt": "string"
}
```

### Success Response (200)
_No response body._

### Error Response (400 | 401)
```json
{
  "message": "string"
}
```

---

## PATCH /chat/read
Read a chat.

### Headers
```json
Token: <your-token>
```

### Success Response (200)
_No response body._

### Error Response (400 | 401)
```json
{
  "message": "string"
}
```

---

## Session
- POST /session
- GET /session
- GET /session/:id
- GET /sesion/:id/admin

---

## POST /session
Generate new session id.

### Success Response (200)
```json
{
  "sessionId": "string"
}
```

### Error Response (400)
```json
{
  "message": "string"
}
```

---

## GET /session/check
Validate session id.

### Headers
```
SessionId: <your-sessionid>
```

### Success Response (200)
```json
{
  "sessionId": "string"
}
```

### Error Response (400 | 401)
```json
{
  "message": "string"
}
```

---

## GET /session/:id
Get session chats.

### Headers
```
SessionId: <your-sessionid>
```

### Success Response (200)
```json
[
  {
    "sessionId": "string",
    "role": "string",
    "message": "string",
    "createdAt": "string"
  }
]
```

### Error Response (400 | 401)
```json
{
  "message": "string"
}
```

---

## GET /session/:id/admin
Get session chats.

### Headers
```
Token: <your-token>
```

### Success Response (200)
```json
[
  {
    "sessionId": "string",
    "role": "string",
    "message": "string",
    "createdAt": "string"
  }
]
```

### Error Response (400 | 401)
```json
{
  "message": "string"
}
```
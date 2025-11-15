# API Documentation
All API prefixed with **/api**

## Authentication
- [POST /register](#post-register)
- [POST /login](#post-login)
- [POST /token](#post-token)

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

## POST /token
Validate token.

### Headers
```
Token: <token>
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
- [GET /chat](#get-chat)
- [POST /chat/admin](#post-chatadmin)
- [POST /chat/user](#post-chatuser)
- [PATCH /chat/read](#patch-chatread)

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
```
Token: <token>
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
```
SessionId: <sessionid>
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
```
Token: <token>
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
- [POST /session](#post-session)
- [GET /session/check](#get-sessioncheck)
- [GET /session/:id](#get-sessionid)
- [GET /session/:id/admin](#get-sessionidadmin)

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
SessionId: <sessionid>
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
SessionId: <sessionid>
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
Token: <token>
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
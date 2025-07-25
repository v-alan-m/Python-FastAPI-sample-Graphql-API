# Python FastAPI sample Graphql API
Python FastAPI sample Graphql API

# 🐍 Python FastAPI + Strawberry GraphQL API

A simple and lightweight GraphQL API built with **FastAPI**, **Strawberry**, and **SQLModel**, demonstrating basic CRUD operations for `User` and `Post` models using a SQLite database.

## ✨ Features

- ⚡️ FastAPI for high-performance web API
- 🍓 Strawberry GraphQL for schema-first GraphQL implementation
- 🗃️ SQLite + SQLModel for simple ORM-style persistence
- 🔄 GraphQL queries and mutations to:
  - ➕ Create users and posts
  - 🔍 Retrieve users and their associated posts
- 🧪 Easily testable via the interactive GraphQL playground

---

## 📦 Dependencies

- Install the necessary dependencies with:
```bash
pip install strawberry-graphql fastapi uvicorn sqlmodel
```
- Install graphql using strawberry
```bash
pip install strawberry-graphql
```

## 🚀 Run the application
- Use the following command to start the FastAPI server with hot-reload:
```bash
uvicorn main:app --reload --no-use-colors
```

## 🔍 Find the interactive GraphQL swagger page
### Visit the local hosted page

- http://127.0.0.1:8000
### Visit the local GraphQL endpoint:
- http://127.0.0.1:8000/graphql

## ✅ Test Examples
###Create a mutation
#### Create user Alice:
- **Input**
```bash
mutation{
  createUser(name: "Alice", email: "alice@example.com") {
    id
    name
    email
  }
}
```
- **Output**:
```json
{
  "data": {
    "createUser": {
      "id": 1,
      "name": "Alice",
      "email": "alice@example.com"
    }
  }
}
```
#### Create user Eric:
- **Input**
```bash
mutation{
  createUser(name: "Eric", email: "eric@example.com") {
    id
    name
    email
  }
}
```
- **Output**
```json
{
  "data": {
    "createUser": {
      "id": 1,
      "name": "Eric",
      "email": "eric@example.com"
    }
  }
}
```
#### Create new post for Eric:
- **Input**
```bash
mutation{
  createPost(title: "New Post", content: "This is a new post", authorId: "2") {
    id
    title
    content
  }
}
```
- **Output**
```json
{
  "data": {
    "createUser": {
      "id": 1,
      "title": "New Post",
      "content": "This is a new post"
    }
  }
}
```
#### Get all information about idNum=2 [Eric]:
- **Input**
```bash
{
  getUser(idNum: 2)  {
    id
    name
    email
    posts 
  {
    id
    title
    content
  }
}
}
```
- **Output**
```json
{
  "data": {
    "getUser": {
      "id": 2,
      "name": "Eric",
      "email": "eric@example.com",
      "posts": [
        {
          "id": 1,
          "title": "New Post",
          "content": "This is a new post"
        }
      ]
    }
  }
}
```
#### Only get name and email for idNum=2 [Eric]:
- **Input**
```bash
{
  getUser(idNum: 2)  {
    name
    email

}
}
```
- **Output**
```bash
{
  "data": {
    "getUser": {
      "name": "Eric",
      "email": "eric@example.com"
    }
  }
}
```
####Only get name and email for idNum=1 [Alice]:
- **Input**
```bash
{
  getUser(idNum: 1)  {
    name
    email

}
}
```
- **Output**
```json
{
  "data": {
    "getUser": {
      "name": "Alice",
      "email": "alice@example.com"
    }
  }
}
```

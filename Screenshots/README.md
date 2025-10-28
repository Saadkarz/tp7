# Screenshots Guide

This folder contains screenshots demonstrating the JAX-RS REST API application.

## ✅ Available Screenshots

### 1. Results.png
- Application console output showing Spring Boot startup
- Shows Jersey initialization and sample data loading
- **Status**: ✅ Available

### 2. Get request Json.png
- GET request to `/banque/comptes`
- Response in JSON format showing list of accounts
- **Status**: ✅ Available

### 3. Get request XML.png
- GET request to `/banque/comptes`
- Response in XML format showing list of accounts
- Header: `Accept: application/xml`
- **Status**: ✅ Available

## 📋 Optional Additional Screenshots

You can add more screenshots to demonstrate additional features:

### get-by-id.png (Optional)
- GET request to `/banque/comptes/1`
- Response showing single account details

### post-create.png (Optional)
- POST request to `/banque/comptes`
- Request body with new account data
- Response showing created account with generated ID

### put-update.png (Optional)
- PUT request to `/banque/comptes/{id}`
- Request body with updated account data
- Response showing updated account

### delete.png (Optional)
- DELETE request to `/banque/comptes/{id}`
- Response showing successful deletion

### h2-console.png (Optional)
- H2 database console at http://localhost:8080/h2-console
- SQL query result showing COMPTE table data

### project-structure.png (Optional)
- IDE view showing complete project structure
- All packages and Java files visible

## How to Take Screenshots

1. **Start the application**: `mvnw.cmd spring-boot:run`
2. **Use Postman or browser** to test each endpoint
3. **Capture screenshots** using:
   - Windows: `Win + Shift + S` (Snipping Tool)
   - Or use Snip & Sketch
4. **Save files** in this folder with the exact names listed above
5. **Format**: PNG recommended for best quality

## Example Postman Requests

### GET All Accounts
```
GET http://localhost:8080/banque/comptes
Accept: application/json
```

### POST Create Account
```
POST http://localhost:8080/banque/comptes
Content-Type: application/json
Accept: application/json

Body:
{
  "solde": 1500.50,
  "dateCreation": "2025-10-28",
  "type": 1
}
```

### PUT Update Account
```
PUT http://localhost:8080/banque/comptes/1
Content-Type: application/json
Accept: application/json

Body:
{
  "solde": 2500.75,
  "dateCreation": "2025-10-28",
  "type": 0
}
```

### DELETE Account
```
DELETE http://localhost:8080/banque/comptes/1
```

---

Once all screenshots are added, they will automatically appear in the main README.md file!


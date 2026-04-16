3. Register an ADMIN user

Using Postman, register a new user with both USER and ADMIN roles using the /api/auth/register endpoint:

http://localhost:8080/api/auth/register
```json
{
    "username": "user3",
    "password": "213",
    "roles": ["ADMIN", "USER"]
}
```
<img width="1283" height="798" alt="image" src="https://github.com/user-attachments/assets/e750dff5-86f2-4ac1-8aec-5553cdb27eb3" />

4. Test Scenario 1 — ADMIN can delete (must pass)

Log in as the admin user, copy the JWT token, and make a DELETE request to /api/books/{id} with the token in the Authorization header. The book should be deleted successfully and return 200 OK.

LOGIN http://localhost:8080/api/auth/login
```json
{
    "username": "user3",
    "password": "213"
}
```
<img width="1283" height="802" alt="image" src="https://github.com/user-attachments/assets/0c9d7af3-d496-41b6-bc68-2a645ff8efc2" />


DELETE http://localhost:8080/api/books/69e03d43985189682f90d702 using user3's token.
<img width="1281" height="799" alt="image" src="https://github.com/user-attachments/assets/ad55cacd-31db-4850-ace8-3ae026e67447" />

Now book three is missing from the database. 
<img width="1919" height="1034" alt="image" src="https://github.com/user-attachments/assets/3a266e1d-9078-4374-b45e-e2410c6a392a" />



5. Test Scenario 2 — USER cannot delete (must pass)

Register a second user with only the USER role. Log in as that user, copy the JWT token, and make a DELETE request to /api/books/{id} with that token. The response must be 403 Forbidden — not 401 Unauthorized. Include the proper Spring Security exception message in the response body.

REGISTER http://localhost:8080/api/auth/register
```json
{
    "username": "user4",
    "password": "312",
    "roles": ["USER"]
}
```
<img width="1284" height="798" alt="image" src="https://github.com/user-attachments/assets/a762752d-b75e-4291-8dbc-cc2080c5daa7" />

LOGIN http://localhost:8080/api/auth/login
<img width="1278" height="803" alt="image" src="https://github.com/user-attachments/assets/4e74385e-3cde-4d79-ab86-827261c6cdfa" />

DELETE http://localhost:8080/api/books/69e03d59985189682f90d704 using user4's token 
<img width="1919" height="1034" alt="image" src="https://github.com/user-attachments/assets/c2bd7157-455e-464c-863a-c73eb99a4095" />








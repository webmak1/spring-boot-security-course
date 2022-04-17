# [Amigoscode, Nelson] Spring Security | FULL COURSE [ENG, 2019]

<br/>

### Lets Build an API

http://localhost:8080/api/v1/students/2/


<br/>

### Installing Spring Security


http://localhost:8080/login/


http://localhost:8080/logout/


<br/>

## Basic Auth

<br/>

### Ant Matches

<br/>

### Application Users


<br/>

### In Memory User Details Manager

<br/>

### Password Encoding With Bcrypt

```
Login: annasmith
Password: password
```

<br/>

### Roles and Permissions

<br/>

### Admin User


<br/>

### Roles & Permissions Using Enums

<br/>

### Role Based Authentication


Linda has not access, but Anna has


http://localhost:8080/api/v1/students/2/


<br/>

## Permission Based Authentication

<br/>

### Management API

<br/>

### Disabling CSRF


<br/>

```
// GET
$ curl -u linda:password123 \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8080/management/api/v1/students \
    | jq
```

<br/>

```
[
  {
    "studentId": 1,
    "studentName": "James Bond"
  },
  {
    "studentId": 2,
    "studentName": "Maria Jones"
  },
  {
    "studentId": 3,
    "studentName": "Anna Smith"
  }
]
```

<br/>

```
// GET
$ curl -u tom:password123 \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8080/management/api/v1/students \
    | jq
```


<br/>

```
// PUT
$ curl -u tom:password123 \
    --header "Content-Type: application/json" \
    --data '{
      "studentName":"Alex Gomes"}' \
    --request PUT \
    --url http://localhost:8080/management/api/v1/students/1 \
    | jq
```


<br/>

```
// POST
$ curl -u tom:password123 \
    --header "Content-Type: application/json" \
    --data '{
      "studentName":"Alex Gomes"}' \
    --request POST \
    --url http://localhost:8080/management/api/v1/students \
    | jq
```

<br/>

### hasAuthority()


<br/>

### Adding Authorities to Users


<br/>

### Permission Based Authentication in Action


<br/>

```
// Tom
// GET
$ curl -u tom:password123 \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8080/management/api/v1/students \
    | jq
```

<br/>

```
// Tom
// FORBIDDEN
// PUT
$ curl -u tom:password123 \
    --header "Content-Type: application/json" \
    --data '{
      "studentName":"Alex Gomes"}' \
    --request PUT \
    --url http://localhost:8080/management/api/v1/students/1 \
    | jq
```


<br/>

```
// Tom
// FORBIDDEN
// POST
$ curl -u tom:password123 \
    --header "Content-Type: application/json" \
    --data '{
      "studentName":"Alex Gomes"}' \
    --request POST \
    --url http://localhost:8080/management/api/v1/students \
    | jq
```


<br/>

```
// Linda
// OK
// POST
$ curl -u linda:password123 \
    --header "Content-Type: application/json" \
    --data '{
      "studentName":"Alex Gomes"}' \
    --request POST \
    --url http://localhost:8080/management/api/v1/students \
    | jq
```

<br/>

### Order Does Matter

<br/>

### preAuthorize()

// SAME CHECKS

<br/>

### Understanding CSRF

<br/>

### CSRF Token


<br/>

```
// Linda
// GET
$ curl -v -u linda:password123 \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://192.168.1.9:8080/management/api/v1/students \
    | jq
```


<br/>

```
// Linda
// OK
// POST
$ curl -u linda:password123 \
    --header "Content-Type: application/json" \
    --data '{
      "studentName":"Alex Gomes"}' \
    --request POST \
    --url http://localhost:8080/management/api/v1/students \
    | jq
```

<!--
    --cookie-jar /tmp/cookies.txt \
-->

Works without token. Cant receive token from server

```
--header "X-XSRF-TOKEN: <TOKEN>"
```

<br/>

### How CSRF Token Generation Works


<br/>

## Form Based Authentication


<br/>

### Enable Form Based Authentication


<br/>

### Session ID

http://localhost:8080/login


<br/>

### Redirect After Success Login

<br/>

### Remember Me

<br/>

### Remember me Cookie and Extra Options

<br/>

### Logout

<br/>

### Logout Button

<br/>

### Password, UserName, Remember-Me, Parameters


<br/>

## DB Authentication Overview

<br/>

### Application User Class

<br/>

### Application User DAO Interface

<br/>

### Fake Application User Service

<br/>

### DAO Authentication Provider

<br/>

### DB Authentication In Action


<br/>

## Intro to JSON Web Token (JWT)


<br/>

### JWT Library

https://github.com/jwtk/jjwt


<br/>

### JWT Filter & Attempt Authentication

<br/>

### JWT Filter & Successful Authentication

<br/>

### Request Filters

<br/>

### Filters and Stateless Sessions

<br/>

### JWT Username and Password Filter


<br/>

```
// LOGIN linda
// POST
$ curl -v \
    --data '{
      "username":"linda",
      "password":"password"}' \
    --header "Content-Type: application/json" \
    --request POST \
    --url http://localhost:8080/login \
    | jq
```

<br/>

### JWT Token Verifier Filter

<br/>

### JWT Token Verifier Filter in Action

<br/>

```
$ export AUTH_TOKEN=eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJsaW5kYSIsImF1dGhvcml0aWVzIjpbeyJhdXRob3JpdHkiOiJzdHVkZW50OndyaXRlIn0seyJhdXRob3JpdHkiOiJzdHVkZW50OnJlYWQifSx7ImF1dGhvcml0eSI6ImNvdXJzZTpyZWFkIn0seyJhdXRob3JpdHkiOiJST0xFX0FETUlOIn0seyJhdXRob3JpdHkiOiJjb3Vyc2U6d3JpdGUifV0sImlhdCI6MTY1MDIxNDUzOCwiZXhwIjoxNjUxMzUyNDAwfQ.tAV_Ol1Oukx2eMkmvlw3yEU5_x-iG-DXMm1R_eFNYiBHWL8iHpr3jvXyH773UIbru7gS87Ja5DqXKDJYWJcx-g


$ echo ${AUTH_TOKEN}
```

<br/>

```
// OK
// GET
$ curl -v \
    --header "Content-Type: application/json" \
    --header "Authorization: Bearer ${AUTH_TOKEN}" \
    --request GET \
    --url http://localhost:8080/management/api/v1/students \
    | jq
```

<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://javadev.org/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://javadev.ru/chat/">Телеграм чат</a>
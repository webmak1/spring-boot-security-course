# [Amigoscode, Nelson] Spring Security | FULL COURSE [ENG, 2019]

<br/>

### Lets Build an API

http://localhost:8080/api/v1/students/2/


<br/>

### Installing Spring Security


http://localhost:8080/login/


http://localhost:8080/logout/


<br/>

### Basic Auth

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

### Permission Based Authentication

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



<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://javadev.org/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://javadev.ru/chat/">Телеграм чат</a>
# ⚡ JavaScript Fetch Cheat Sheet

## 📡 Basic GET request

```javascript
fetch("/api.php")
  .then(res => res.json())
  .then(data => {
    console.log(data);
  });
```

---

## 📡 GET with async/await (recommended)

```javascript
async function getData() {
  const res = await fetch("/api.php");
  const data = await res.json();
  console.log(data);
}
```

---

## 📤 POST JSON (most common API use)

```javascript
fetch("/api.php", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    email: "test@example.com",
    password: "123456"
  })
})
.then(res => res.json())
.then(data => console.log(data));
```

---

## 📤 POST JSON (async/await)

```javascript
async function login() {
  const res = await fetch("/api.php", {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      email: "test@example.com",
      password: "123456"
    })
  });

  const data = await res.json();
  console.log(data);
}
```

---

## ⚠️ Error handling (IMPORTANT)

```javascript
fetch("/api.php")
  .then(res => {
    if (!res.ok) {
      throw new Error("Network error");
    }
    return res.json();
  })
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

---

## 🍪 Fetch with PHP sessions (cookies)

```javascript
fetch("/api.php", {
  method: "POST",
  credentials: "include"
});
```

Use this when PHP sessions are involved.

---

## 📄 Sending FormData (file uploads / forms)

```javascript
const formData = new FormData();
formData.append("email", "test@example.com");
formData.append("password", "123456");

fetch("/api.php", {
  method: "POST",
  body: formData
});
```

🚨 Don’t set `Content-Type` manually here.

---

## 🔍 Reading different response types

### JSON (most APIs)

```javascript
res.json()
```

### Plain text

```javascript
res.text()
```

### Raw binary

```javascript
res.blob()
```

---

## 📦 Common API patterns

### ✔ success boolean API

```javascript
if (data === true) {
  console.log("success");
}
```

---

### ✔ structured API (better)

```json
{
  "success": true,
  "message": "Login OK"
}
```

```javascript
if (data.success) {
  console.log(data.message);
}
```

---

## 🧠 Pro tips

* Always use `res.json()` unless you KNOW it's text
* Always check `res.ok` for errors
* Use `async/await` for cleaner code
* Use `credentials: "include"` for PHP sessions
* Never forget `JSON.stringify()` for JSON POST

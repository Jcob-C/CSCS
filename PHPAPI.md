# ⚡ PHP API + MySQL Cheat Sheet

## 🧱 1. Basic JSON API response

```php id="p0v8x2"
header("Content-Type: application/json");

echo json_encode([
  "success" => true,
  "message" => "Hello world"
]);
```

---

## 🗄️ 2. Database connection (mysqli)

```php id="k2v9ma"
$conn = new mysqli("localhost", "db_user", "db_pass", "db_name");

if ($conn->connect_error) {
  die(json_encode([
    "success" => false,
    "error" => "DB connection failed"
  ]));
}
```

---

## 📥 3. Read JSON input (POST API)

```php id="9f2kq1"
$data = json_decode(file_get_contents("php://input"), true);

$email = $data["email"] ?? "";
$password = $data["password"] ?? "";
```

---

## 🔎 4. SELECT (get data)

### Get one user

```php id="c8x1lm"
$stmt = $conn->prepare("SELECT id, email FROM users WHERE email = ?");
$stmt->bind_param("s", $email);
$stmt->execute();

$result = $stmt->get_result();
$user = $result->fetch_assoc();

echo json_encode($user ? $user : false);
```

---

### Get multiple rows

```php id="z1q8wp"
$result = $conn->query("SELECT id, email FROM users");

$rows = [];

while ($row = $result->fetch_assoc()) {
  $rows[] = $row;
}

echo json_encode($rows);
```

---

## ➕ 5. INSERT (create data)

```php id="m4v7ta"
$stmt = $conn->prepare("INSERT INTO users (email, password) VALUES (?, ?)");
$stmt->bind_param("ss", $email, $password);

if ($stmt->execute()) {
  echo json_encode([
    "success" => true,
    "id" => $stmt->insert_id
  ]);
} else {
  echo json_encode([
    "success" => false
  ]);
}
```

---

## ✏️ 6. UPDATE

```php id="q9m2xn"
$stmt = $conn->prepare("UPDATE users SET password = ? WHERE email = ?");
$stmt->bind_param("ss", $password, $email);

echo json_encode([
  "success" => $stmt->execute()
]);
```

---

## ❌ 7. DELETE

```php id="v5k8lp"
$stmt = $conn->prepare("DELETE FROM users WHERE email = ?");
$stmt->bind_param("s", $email);

echo json_encode([
  "success" => $stmt->execute()
]);
```

---

## 🔐 8. Login check (password safe)

```php id="t3kq9a"
$stmt = $conn->prepare("SELECT password FROM users WHERE email = ?");
$stmt->bind_param("s", $email);
$stmt->execute();

$result = $stmt->get_result();

if ($row = $result->fetch_assoc()) {
  if (password_verify($password, $row["password"])) {
    echo json_encode(["success" => true]);
  } else {
    echo json_encode(["success" => false]);
  }
} else {
  echo json_encode(["success" => false]);
}
```

---

## 🍪 9. Session login

```php id="n7x2pq"
session_start();

$_SESSION["user_id"] = 123;

echo json_encode(["success" => true]);
```

---

## 🔍 10. Check session auth

```php id="u1m8zd"
session_start();

if (!isset($_SESSION["user_id"])) {
  echo json_encode([
    "success" => false,
    "error" => "not_logged_in"
  ]);
  exit;
}

echo json_encode([
  "success" => true,
  "user_id" => $_SESSION["user_id"]
]);
```

---

## ⚠️ 11. Standard API response pattern (recommended)

```php id="x2q8nv"
function response($success, $data = null, $error = null) {
  echo json_encode([
    "success" => $success,
    "data" => $data,
    "error" => $error
  ]);
  exit;
}
```

### Usage:

```php id="b9v2lk"
response(true, ["id" => 1]);
response(false, null, "Invalid login");
```

---

## 🧠 Best practices (important)

* Always use `prepare()` → prevents SQL injection
* Always return JSON (`Content-Type: application/json`)
* Use `password_hash()` + `password_verify()`
* Never trust raw input (`$_POST` or JSON)
* Use consistent API format (`success + data + error`)

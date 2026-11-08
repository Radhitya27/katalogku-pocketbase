# KatalogKu API Contract

Base URL:
http://10.46.30.164:8080/api

## 1. Products

### GET /products
Mengambil daftar produk.

Query:
- perPage=5
- sort=-created

Auth: Public

### GET /products?filter=title~'kopi'
Mencari produk berdasarkan judul.

Auth: Public

### GET /products/:id
Mengambil detail produk berdasarkan ID.

Auth: Public

## 2. Account

### POST /auth/records
Registrasi akun baru.

Body:
{
  "name": "Budi",
  "email": "budi@example.com",
  "password": "passwordku123",
  "passwordConfirm": "passwordku123"
}

Auth: Public

### POST /auth/auth-with-password
Login pengguna.

Body:
{
  "identity": "budi@example.com",
  "password": "passwordku123"
}

Auth: Public

Response: token dan record pengguna.

## 3. Favorites

Seluruh request favorit membutuhkan:
Authorization: <token>

### GET /favorites
Mengambil favorit milik pengguna yang sedang login.

### POST /favorites
Menambahkan produk ke favorit.

Body:
{
  "user": "<user_id>",
  "product_id": "<product_id>"
}

### DELETE /favorites/:id
Menghapus favorit berdasarkan ID record.

Response sukses: HTTP 204.

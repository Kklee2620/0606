# 📦 Dự Án Website Thương Mại Điện Tử - README dành cho Developer (No Docker)

## 🔰 Mục Tiêu

Xây dựng nền tảng web thương mại điện tử gồm:
- **Giao diện Người dùng (Web Client)**
- **Trang quản trị (Admin Panel)**

---

## 🖼️ 1. Thiết Kế UI

| Thành phần    | Giá trị                               |
| ------------- | ------------------------------------- |
| Thiết bị      | Desktop / Tablet / Mobile             |
| Phong cách    | 3D hiện đại, Glassmorphism            |
| Font          | Poppins, Inter, SF Pro Display        |
| Màu chính     | #5D5FEF, #FFFFFF, #F4F5F7, #FF5A5F     |
| Hiệu ứng      | Hover 3D, soft-shadow, carousel       |

---

## 🧩 2. Chức Năng Chính

### Web Client

- **Home**: Header, slider, danh mục, sản phẩm đề xuất
- **Category**: Breadcrumb, lọc, phân trang
- **Product Detail**: Ảnh zoom, tùy chọn màu/size, mô tả, đánh giá
- **Cart**: Sửa số lượng, mã giảm giá
- **Checkout**: One-page hoặc step-by-step
- **Account**: Thông tin, đơn hàng, wishlist, địa chỉ

### Admin Panel

- **Dashboard**: Doanh thu, đơn hàng, cảnh báo
- **Product Manager**: CRUD sản phẩm, drag/drop ảnh, biến thể
- **Order Manager**: Trạng thái, in vận đơn, hoàn tiền
- **User Manager**: Khách hàng, phân quyền nhân viên
- **Reports**: Thống kê xuất Excel/PDF
- **Settings**: Cài đặt giao diện, thanh toán, vận chuyển

---

## ⚙️ 3. Công Nghệ & Kiến Trúc

| Layer      | Stack                              |
|------------|------------------------------------|
| Frontend   | Next.js + TailwindCSS + Zustand    |
| Backend    | Node.js + Express.js               |
| Database   | PostgreSQL                         |
| API        | RESTful API                        |
| CI/CD      | GitHub Actions                     |

---

## 📁 4. Sơ Đồ Thư Mục

```

ecommerce-platform/
├── client/        # Giao diện người dùng
├── admin/         # Trang admin
├── api/           # Backend API
├── prisma/        # ORM schema
├── docs/          # Swagger, hướng dẫn
├── .github/       # GitHub Actions workflow
├── .env.example   # Mẫu file cấu hình môi trường

```

---

## 🧱 5. Cấu Trúc CSDL

```

USERS, ADDRESSES, PRODUCTS, PRODUCT\_VARIANTS,
ORDERS, ORDER\_ITEMS, CATEGORIES, REVIEWS, COUPONS

````

---

## 🔗 6. REST API Mẫu

| Method | Endpoint            | Mô tả                 |
|--------|---------------------|------------------------|
| GET    | /products           | Danh sách sản phẩm     |
| POST   | /cart/add           | Thêm vào giỏ hàng      |
| POST   | /checkout           | Tạo đơn hàng mới       |
| POST   | /admin/products     | Tạo sản phẩm (Admin)   |

---

## 🧪 7. Testing

| Loại      | Công cụ          |
|-----------|------------------|
| Unit      | Jest, Vitest     |
| API       | Supertest        |
| UI        | Cypress          |

---

## 🔒 8. Bảo mật & Role

- JWT Auth (User & Admin)
- Route middleware theo quyền truy cập
- 2FA cho admin (tùy chọn)

---

## ⚙️ 9. CI/CD (GitHub Actions)

```yaml
name: Node.js CI

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3
      - name: Setup Node
        uses: actions/setup-node@v3
        with:
          node-version: '18.x'
      - run: npm install
      - run: npm test
      - run: npm run lint
````

---

## 📘 10. Swagger (docs/swagger.yaml)

```yaml
openapi: 3.0.1
info:
  title: E-Commerce API
paths:
  /products:
    get:
      summary: Get all products
  /cart/add:
    post:
      summary: Add to cart
components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
```

---

## 🧰 11. Khởi chạy Local (Không Docker)

1. Cài PostgreSQL local
2. Tạo DB `ecommerce_dev`
3. Tạo `.env` từ `.env.example`:

   ```
   DATABASE_URL=postgres://postgres:password@localhost:5432/ecommerce_dev
   ```
4. Cài & chạy:

   ```bash
   cd api && npm install && npm run dev
   cd client && npm install && npm run dev
   cd admin && npm install && npm run dev
   ```

---

Bạn có thể sao chép file này trực tiếp để dùng làm nền tảng triển khai. Nếu cần mẫu `.env.example`, schema Prisma hoặc script seed dữ liệu, mình có thể bổ sung thêm.

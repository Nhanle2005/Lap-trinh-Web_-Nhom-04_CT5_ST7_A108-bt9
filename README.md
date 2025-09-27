1. Clone và chạy dự án

```bash
# 1. Điều hướng đến thư mục dự án
cd d:\wb1\demoSpringbootCT5ST7-3

# 2. Compile dự án
mvn clean compile

# 3. Chạy ứng dụng
mvn spring-boot:run
```

2. Kiểm tra khởi động thành công
Các URL để test

Trang chủ | http://localhost:8080/ | Dashboard chính |
Quản lý Sản phẩm | http://localhost:8080/products | CRUD sản phẩm |
Quản lý Danh mục | http://localhost:8080/categories | CRUD danh mục |
Quản lý Người dùng | http://localhost:8080/users | CRUD người dùng |
| GraphQL API | http://localhost:8080/graphql | POST endpoint |

Test GraphQL Queries

Lấy sản phẩm theo giá (thấp → cao)
```graphql
query {
  getAllProductsByPriceAsc {
    id
    title
    price
    quantity
    category { name }
    user { fullname }
  }
}
```

Lấy sản phẩm theo danh mục
```graphql
query {
  getProductsByCategory(categoryId: "1") {
    id
    title
    price
    desc
    user { fullname }
  }
}
```

Tạo sản phẩm mới
```graphql
mutation {
  createProduct(input: {
    title: "Sản phẩm mới"
    quantity: 10
    desc: "Mô tả sản phẩm"
    price: 500000
    userId: "1"
    categoryId: "1"
  }) {
    id
    title
    price
  }
}
```

Lấy tất cả danh mục
```graphql
query {
  getAllCategories {
    id
    name
    images
  }
}
```




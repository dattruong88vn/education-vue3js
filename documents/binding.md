## Binding Text (có 2 cách)

#### 1. Mustache Syntax:

Sử dụng 2 cặp dấu ngoặc nhọn (curly braces): `<div>{{ name }}</div>`

#### 2. Directive:

Trong view, mỗi directive đều có một tiền tố `v-`.
Để binding text sử dụng directive có cấu trúc như sau: `v-text="<data-name>"`.
Vue sẽ thay thế content (text hoặc children) của thẻ HTML bằng data value, nếu cố tình thêm content thị sẽ bị lỗi.

Ví dụ:

```
<div v-text="channel"></div>
```

#### 3. Tổng kết

Nên sử dụng Mustache Syntax, dễ đọc và performance tốt hơn so với directive v-text.

---

## Binding HTML

Sử dụng directive `v-html="<data-name>"`.
Cần cẩn thận khi sử dụng v-html directive, đặc biệt với các đoạn script của bên thứ ba, nó có thể chứa mã độc.

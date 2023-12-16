### 4 cách để thêm Vue vào project

###### 1. CDN

- Nhúng đường dẫn CDN của view vào file HTML trong thẻ script
- `<script src="https://unpkg.com/vue@next"></script>`

###### 2. Sử dụng npm

- Dùng câu lệnh: `npm install vue@next`
- Ưu tiên sử dụng npm nếu dự án có quy mô lớn.

###### 3. Sử dụng CLI:

- Vue cung cấp CLI (command line interface) để có thể nhanh chóng build SPA.
- 2 câu lệnh như sau:

```
npm install -g @vue/cli

vue create <project-name>
```

###### 4. Sử dụng Vite

- Câu lệnh: `npm init vite-app <project-name>`

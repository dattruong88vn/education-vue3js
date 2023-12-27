## Component

#### Giới thiệu chung

Vue cũng build UI dựa trên kiến trúc Component.

Có nghĩa là sẽ chia nhỏ UI thành nhiều thành phần khác nhau (mỗi thành phần là 1 component).

Mỗi vue application đều có một Root Component, được viết trong file `App.vue`, đây là Component gốc chưa tất cả những component khác như Header, Footer, Sidebar, MainContent.

#### Các thành phần của một component

Mỗi component được viết trong 1 file `.vue`, bao gồm 3 thành phần là `template`, `script` và `style`.

- `template`: hiển thị cấu trúc HTML
- `script`: logic của component
- `style`: style css của component

Ví dụ:

```
// Parent Component
<template>
    <Greet name="Diana" hero-name="Wonder Woman" />
    <Greet :name="name" :hero-name="heroName" />
</template>

// Greet Component
<template>
  <div>
    <h2>Hello {{ name }} a.k.a {{ heroName }}</h2>
  </div>
</template>

<script>
export default {
  name: "greet-component",
  props: {
    name: String,
    heroName: String,
  },
};
</script>
```

Trong ví dụ trên, component Greet nhận vào 2 props là `name` và `hero-name`.

- Props name có thể truyền vào theo dạng `camelCase` hoặc `kebab-case`. Trong component Greet sẽ khai báo props về dạng `camelCase`.

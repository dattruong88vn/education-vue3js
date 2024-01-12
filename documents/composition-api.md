## COMPOSITION API

#### Định nghĩa

Composition API là một tính năng mới trong Vue 3, giúp chúng ta có thể viết component theo một cách khác, cụ thể ở đây là thẻ `script`.

Những video từ đầu đến giờ, chúng ta sử dụng `OPTIONS API`, bao gồm các thuộc tính nằm bên trong object được export defaut của thẻ `script` như: data(), computed, method, watchers, life cycle hook.

Sử dụng `Options API` là một cách để build Vue Component. Và một cách khác đó là sử dụng `Composition API`.

Khi build một Vue Component, bạn có thể lựa chọn 1 trong 2 cách trên đều được.

#### Lý do xuất hiện của Composition API

Có 2 lý do:

1. Nếu sử dụng `Options API`, khi Vue project được mở rộng và phát triển, sẽ trở nên rất khó quản lý và maintain.

Trong `Options API`, components được tổ chức theo các options trong export default object như data(), computed, methods, created, mounted. Mỗi options chứa các data hay logic của nhiều tính năng khác nhau.

Logic trong component không được gom nhóm theo feature, khiến cho code rất khó đọc khi component ngày càng lớn hơn (tương tự vấn đề trong React khi sử dụng Class Component, các feature phải sử dụng chung Life Cyclye Methods như `componentDidMount`, `componentDiđUpate`, `componentWillUnmount`...).

2. Việc tái sử dụng logic giữa các Component thực sự rất khó.

Mặc dù cả Vue 2 và Vue 3 đều cung cấp tính năng `Mixins` để thực hiện điều này nhưng nó có rất nhiều hạn chế.

Để khắc phục điều này, `Composition API` được giới thiệu trong Vue 3.

#### Cách sử dụng

###### Replace Data Property

Vue Component có thể kết hợp giữa Options API và Composition API cùng lúc.

Trong thẻ script, import `ref` function từ `vue`. Function này khác với `template ref` dùng để tạo reference đến 1 thẻ HTML hoặc Component con.

Trong export default object, thêm vào function `setup`.

- Tạo một reactive reference: `const c_firstName = ref("Initial Name");`
- Để binding được data này vào thẻ template, cần return nó trong `setup` function:

```
setup() {
  const c_firstName = ref("Initial Name");

  return {
      c_firstName
  }
}
```

`c_firstName` không chỉ là 1 string, nó là một object có chứa key value. Trong `setup function`, hoàn toàn có thể update giá trị của nó (mutate) hoặc tạo ra một data mới (tương tự như computed trong option API).

```
setup() {
  const c_firstName = ref("Initial Name");
  c_firstName.value = "new name";

  const greet = `Hello ${c_firstName.value}`

  return {
      c_firstName,
      greet
  }
}
```

Khi hiển thị data từ Compotion API, trong `template` không cần trỏ đến value: `{{ c_firstName.value }}`. Vue sẽ tự unpack và hiển thị đúng value giúp chúng ta `{{ c_firstName }}`

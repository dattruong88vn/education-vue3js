# Slots

#### Định nghĩa

`Slots` khá tương đồng với `children` trong React, với một số điểm như sau:

- Cho phép re-useable component bằng cách truyền vào component con các data khác nhau
- Khác với `props`, `slots` cho phép component cha có thể control được content bên trong component con.
- `slots` còn cho phép component cha nhúng bất cứ content nào vào component con bao gồm cả các thẻ HTML.

###### Cách thực hiện

Ở component cha, thay vì gọi component con bằng self-closing tag `<ConponentCon />` thay thế bằng cặp tag đóng mở `ComponentCon></ComponentCon>`.

Sau đó truyền bất cứ thẻ HTML mong muốn vào giữa 2 thẻ đóng mở.

Bên trong Component con, muốn nhậnd được content này chỉ cần khai báo cặp thẻ `<slot></slot>` bên trong `template` thì phần content được truyền vào sẽ thay thế thẻ `slot` này.

Trường hợp ở component cha ko truyền vào content, thì phần content bên trong thẻ `slot` sẽ được hiển thị.

Ví dụ:

```
// Cha
<ComponentCon>
    String Text
</ComponentCon>
<ComponentCon>
    <h2>String Text in H2 element</h2>
</ComponentCon>

// Con
<template>
    <div>
        <slot>Default Content</slot>
    </div>
</template>
```

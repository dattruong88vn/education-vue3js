## Teleport Component

Mỗi Vue project đều được build bên trong 1 thẻ div `<div id="app"></div>` bên trong file index.html. Tất cả các component trong project khi được render mặc định sẽ nằm trong node này.

Teleport component (tương tự `Portal` trong React) có chức năng render một component cụ thể vào một DOM node cụ thể nằm bất cứ đâu trong DOM tree, có thể nằm ngoài thẻ div root.

Teleport sử dụng cho modal, tooltip... Các component này được render độc lập với app để tránh bị ảnh hưởng bởi CSS của các component cha.

Cú pháp:

Tạo dom node trong file index.html
Wrap component bằng cặp thẻ `teleport`, cùng với thuộc tính `to="<dom-node>"`.

- File index.html

```
    <body>
        <div id="app"></div>
        <div id="modal-root"></div>
    </body>
```

- File App.vue hoặc Component bất kỳ:

```
<teleport to="#modal-root">
    <MyComponent />
</teleport>
```

## Template Ref

Attribute `ref` có thể được khai báo trên một html element hoặc component. Nó sẽ giúp tạo ra một reference đến thẻ html element hoặc component đó giúp chúng ta có thể access một cách nhanh chóng.

Khai báo: <element ref="<labelRef>">...</element>

- `labelRef` là unique để giúp chúng tra truy xuất đến element tương ứng.

Truy xuất, tất cả các `ref` sau khi được khai báo sẽ được lưu vào chung trong một object có tên là `#refs`. Trong `script`, truy xuất bằng cách sau: `this.$refs`

Ví dụ:

```
<template>
    <input type="text" ref="inputRef"/>
</template>
<script>
    export default {
        ...
        mounted() {
            this.$refs.inputRef.focus();
        }
    }
</script>
```

## METHOD

Trong object `export default` của thẻ `<script`, thêm thuộc tính `methods` là một object.

Methods là một object, mỗi key của object này chính là một function có thể sử dụng được bên trong `template` tag.

Lưu ý, các function được khai báo dưới dạng regular function, KHÔNG được sử dụng arrow function. Bởi vì view đã bind các data vào trong các function này. Nếu sử dụng arrow function thì ko thể access đến data

```
<script>
    export default {
        data() {
            return {
                number: 10,
            }
        },
        methods: {
            sum(a, b) {
                return a + b
            },
            multiply(num) {
                return num * this.number
            }
        }
    }
</script>
```

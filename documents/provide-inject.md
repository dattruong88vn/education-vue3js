# Provide and Inject

Tương tự như `context/useContext` trong React, `Provide` và `Inject` là 2 step của quá trình chia sẻ data từ Component Root đến các component con mà không cần truyền qua props của các component trung gian.

Sử dụng để chia sẻ các thông tin như Theme, User data...

#### Các bước thực hiện

###### Provide value trong Root

Trong `export default`, thêm thuộc tính `provide` là một object với những cặp key - value.

Ví dụ:

```
<script>
    export default {
        provide: {
            username: "Thanh Dat",
        },
    }
</script>
```

###### Inject value trong Root

Trong `export default` thêm thuộc tính `inject` là một string array với mỗi phần tử chính là tên `key` được khai báo trong `provide`. Lúc này, mỗi phần tử trong array sẽ được binding thành 1 data với tên tương ứng trong `template`.

Nếu muốn đổi tên key, thay giá trị của `inject` là một object, với `key` là tên mong muốn, `value` chính là tên key được khai báo trong `provide`.

```
// String Array
<script>
    export default {
        name: "ComponentC",
        inject: ["username"],
    };
</script>

// Object
<script>
    export default {
        name: "ComponentC",
        inject: {
            myName: 'username'
        },
    };
</script>
```

#### Provide và Inject trong cùng 1 component

Mặc định, nếu Component A khai báo provide là một `object` thì componentA sẽ không thể nhận được data này.
Để khắc phục, thực hiện 2 bước:

- Khai báo data property (là data muốn provide);
- Thay đổi `provide` thành 1 function và return về một object.

Lúc này trong template của Component A có thể lấy được data muốn `provide` và các component con vẫn có thể `inject`.

```
export default {
  name: "App",
  data() {
    return {
      username: "Thanh Dat",
    };
  },
  provide() {
    return {
      username: this.username,
    };
  },
};
```

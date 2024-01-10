## Mixins

Là một chức năng giúp share logic giữa các component.

#### Đặt vấn đề:

- Chức năng 1: tạo một clickCounter Component, cho phép người dùng click vào button, mỗi lần click tăng biến count lên 1.
- Ta phải tạo 1 component với data-property `count`, giá trị mặc định 0. Methods `increaseCount` tăng count lên 1 và thêm vào event click của button.
- User lại yêu cầu một chức năng khác tương tự clickCounter, nhưng event tăng biến count là hover, keyPress...
- Ta có thể viết nhiều component khác nhau với cùng một logic với clickCounter

#### Vấn đề:

- Logic đang bị viết lặp đi lặp lại, nếu có thay đổi cần maintain hoặc extends phải sửa nhiều chỗ
- Cần share logic của `count` và `increaseCount` giữa các component.

#### Sử dụng Mixins để reuse functionality

###### Bước 1: khai báo mixins

Tạo file `mixins/counter.js` nằm trong thư mục mixins. Lưu ý đây là file `javascript` không phải `vue`.

File JS này export default 1 object, object này chứa các thành phần được export default trong file vue.

Cụ thể là phần data (chứa `count`) và phần methods (chứa `increaseCount`);

`counter.js`

```
export default {
    data() {
        return {
            count: 0
        }
    },
    methods: {
        increaseCount() {
            this.count += 1
        }
    }
}

```

###### Bước 2: import và khai báo mixins trong file vue

- Trong thẻ `script` của các file vue, import file `counter.js`.

```
import CounterMixin from "..../mixins/counter.js"
```

- Xoá tất cả `data` và `methods` liên quan đến phần count trong Vue component

- Phần export default của thẻ `script`, thêm thuộc tính `mixins` có value là một array. Mỗi phần tử trong array chính là object được import từ các file mixins. Trường hợp sử dụng nhiều logic khác nhau từ nhiều file.

```
export default {
    ...
    mixins: [ CounterMixin ]
}
```

#### Lưu ý

- Các thành phần trong `mixins` có thể là tất cả những thành phần được export defaut từ thẻ script trong component như data, computed, methods, các life cycle hook.
- Khi các component nhúng các mixins thì nó sẽ được kết hợp với các thành phần của component.
- Các đoạn code bên trong mixin sẽ được thực thi trước các đoạn code bên trong componetn.
- Khi data, methods giữa mixin và component bị trùng tên thì Vue sẽ ưu tiên cho property nằm trong component.
- Có thể tạo `global mixins` thông qua class Vue: `Vue.mixin({...})`. Lúc này tất cả các component nằm trong project đều sẽ nhận được global mixins.

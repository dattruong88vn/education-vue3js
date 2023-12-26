## Watchers

#### Định nghĩa

Mới nghe tên có vẻ giống `useEffect` trong `React`.

Cho phép chúng ta theo dõi sự thay đổi của `data property` hoặc `computed property`, từ đó thực thi các đoạn code để phản hồi lại sự thay đổi đó.

#### Cách sử dụng

Trong object `export default` của thẻ `<script`, thêm thuộc tính `watch` là một object.

Mỗi thuộc tính trong object `watch` là một `function` hoặc `object` có tên tương ứng với tên của `data property` hoặc `computed property` cần theo dõi sự thay đổi.

###### Trường hợp là function:

`Function` này nhận vào 2 tham số:

- Tham số đầu tiên: chính là giá trị mới được update của data cần theo dõi (trong ví dụ dưới là data property `volume`).
- Tham số thứ hai là giá trị trước đó.

```
<script>
export default {
    name: '',
    data() {
        return {
            volume: 0
        }
    },
    methods: {},
    computed: {},
    watch: {
        volume(newValue, oldValue) {
            // execute some code
        }
    }
}
</script>
```

###### Trường hợp là object:

Object bao gồm các thuộc tính sau:

- `handler`: là một function chứa các đoạn code cần thực thi khi data thay đổi, tham số cũng tương tự trường hợp trên.
- `immediate`: true | false. `true` sẽ thực thi ngay khi Component được mount, ngược lại `false` chỉ thực thi khi data thay đổi.
- `deep`: true | false. `true` theo dõi tất cả các thuộc tính bên trong một object hoặc các phần tử của array, `false` chỉ theo dõi địa chỉ ô nhớ của object hoặc array. Trường hợp thay đổi data bằng cách tạo ra một object hoặc array mới thì không cần thêm thuộc tính `deep`.

#### So sánh Computed Property và Watches

Câu hỏi đặt ra là có thể sử dụng `Watchers` để thay thế cho `Computed Property` hay không?

Câu trả lời là có, `Watchers` đơn giản là cung cấp một cách chung để phản ứng lại sự thay đổi của Data. Tuy nhiên, không khuyến khích sử dụng `Watchers` thay thế cho `Computed Property`.

Theo đánh giá cá nhân, nên sử dụng như sau:

- `Computed Property`: nó tương ứng `useMemo` trong React
  - Dùng để tạo ra data từ những data có sẵn. (fullName = firstName + lastName)
  - Giảm thiểu việc truy xuất vào các thuộc tính trong Object: (d = a.b.c.d)
- `Watchers`: nó tương ứng `useEffect` trong React.
  - dùng để thực thi một số đoạn code khi data thay đổi.
  - Call Api khi data thay đổi.
  - Áp dụng các hiệu ứng CSS.

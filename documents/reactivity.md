## Reactivity trong Vue

#### Định nghĩa

Ví dụ:

- Sử dụng Composition API method `setup()`. Khai báo biến có cùng giá trị theo 2 cách sau và return cả hai để binding vào template

`name`: sử dụng cách khai báo biến của JS với từ khoá let
`nameReactive`: sử dụng ref function của Vue

```
let name = "Initial Name";
const nameReactive = ref("Initial Name");

return {
    name,
    nameReactive
}
```

- Lúc này, UI đều hiển thị được giá trị của cả 2 biến `name` và `nameReactive`.

- Dùng `setTimeout` sau 2 giây update cả 2 giá trị thành `Update Name`.

```
setTimeout(() => {
    name = "Update Name";
    nameReactive.value = "Update Name"
}, 2000);
```

- Sau 2 giây, UI chỉ update được giá trị của biến `nameReactive`.

Đây chính là `Reactivity` trong Vue. Có thể hiểu đơn giản là cơ chế phản ứng khi có sự thay đổi của các `Reactive Reference` để update lại DOM node và hiển thị lên UI.

Trong ví dụ trên, biến `name` là một biến bình thường ko khai báo `reactive reference` nên khi thay đổi sẽ không update lại DOM và UI.

Ngược lại, biến `nameReactive` được khai báo `reactive reference` thông qua `ref` function, nên mỗi khi nó thay đổi, Vue sẽ update lại DOM và re-render lại Component.

Trường hợp khai báo biến bằng `reactive function` cũng tương tự như `ref function`.

Tuy nhiên cần lưu ý là Vue chỉ reactive với object được khai báo bằng `reactive function`. Nếu trong `setup()` function, nếu chỉ binding các thuộc tính riêng lẻ của object đến template thì khi các thuộc tính này thay đổi thỉ Vue Component sẽ không được update và re-render.

Ví dụ:

```
setup() {
    const state = reactive({
        fName: "Dat",
        lName: "Truong"
    });

    setTimeout(() => {
        state.fName = "Dat 09";
        state.lName = "Truong Thanh"
    }, 2000);

    return {
        <!-- Reactive Working -->
        state,

        <!-- Reactive Not Working -->
        fName: state.fName,
        lName: state.lName
    }
}
```

#### Function toRefs

Trường hợp muốn binding từng key của object và vẫn đảm bảo reactivity khi có thay đổi, sử dụng `toRefs() function`, function này nhận vào tham số là `reactive reference object` được tạo ra bằng `reactive function`.

```
setup() {
    const state = reactive({
        fName: "Dat",
        lName: "Truong"
    });

    setTimeout(() => {
        state.fName = "Dat 09";
        state.lName = "Truong Thanh"
    }, 2000);

    return toRefs(state);
}
```

TỰ NHẬN XÉT VỀ FUNCTION `toRefs`:

- Chỉ nhận 1 tham số là `reactive reference object` nên CÓ LẼ không phù hợp nếu có nhiều object được tạo ra từ `reactive` function
- Nó khá bị bó buộc chỉ trong 1 state duy nhất.

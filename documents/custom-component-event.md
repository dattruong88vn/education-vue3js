# Custome Component Event

Tạo ra một custom event của component con, khi event xảy ra sẽ gọi custom event này.

Component Cha sẽ lắng nghe custom event từ component con và thực thi các function tương ứng.

Ví dụ sau open popup từ Cha và close popup từ con, component con sẽ tạo ra một cusctom event để close popup.

#### Các bước thực hiện

- Trong component Con, `export default` thêm một thuộc tính là `emits`, value là một string array với mỗi string là tên của một `custom event`.

Ví dụ:

```
export default {
    emits: ['customEventName']
}
```

- Thêm event vào 1 element, khi event xảy ra sẽ emit `custom event` thông qua function `$emit('customEventName')`.

```
<button @click="emit('customEventName')">Close Button</button>
```

- Component Cha sẽ gắn `custom event` cho Component Con:

```
<ComponentCon @customEventName='doSomeThing'/>
```

#### Thêm params vào custom event

- Ở component Con, trong function `emits`, thêm vào các tham số tiếp theo. Các tham số từ thứ 2 trở đi sẽ trở thành tham số cho các function được lắng nghe ở Component Cha.
- Ở component Cha muốn nhận được các tham số này, phải khai báo function vào trong thuộc tính `methods`

```
// Cha
export default {
  name: "Parent-Comp",
  data() {
    return {
      showPopup: false,
    };
  },
  methods: {
    handleClosePopup(value) {
      this.showPopup = value;
    },
  },
  components: {
    Popup,
  },
};

// Con
<button @click="$emit('closePopup', false)">Close Popup</button>
```

#### Validate Emit Event từ Child Component

Trong Component Con, update `emits` trong export default từ Array sang Object.
Mỗi key trong object này chính là tên của `event` được emit lên component cha, và value là tương ứng là một `function`.
Function nhận vào tham số chính là tham số gửi lên component cha khi emit event --> Validate giá trị trong function này.

```
emits: {
  closePopup: (name) => {
    return !!name;
  },
},
```

Trong ví dụ trên, function return về `true | false`, nếu false thì trên browser sẽ hiển thị `warning: event validation failed for ...`.

#### Component và v-model

- Vue cung cấp `v-model` để sử dụng cùng với form và input.
- Tuy nhiên trong thực tế, không bao giờ chúng ta làm việc trực tiếp với thẻ `input` mặc định của HTML. Thay vào đó, chúng ta sẽ build một `custom input` component để style theo đúng yêu cầu, đồng thời thêm một vài logic để có thể sử dụng trên toàn app.
- Vấn đề đặt ra là làm sao có thể sử dụng `v-model` trên những `custom-input` component này.

```
<Input v-model="name" />
```

Phân tích vấn đề:

- Khi thêm thuộc tính `v-model` cho một `custom-component`, mặc định nó sẽ không hiểu behavior của component.
- Do đó cần phải truyền được data từ `data-property` trong component Cha vào `input` element trong component Con thông qua `v-model`. Đồng thời khi `onChange` data trong `input` element thì sẽ emit một event lên component Cha để update `data-property`.

Cách thực hiện:

- Khi thêm thuộc tính `v-model` cho component Con thì mặc định component Con sẽ nhận được 1 props có tên là `modelValue`. Cần khai báo props này trong Component Con.

```
props: {
  modelValue: String,
},
```

- Ngoài ra, Vue cũng định nghĩa sẵn một `emit-event` khi thêm thuộc tính `v-model` cho component con, chúng ta cũng cần phải khai báo emit cho event này

```
emits: ["update:modelValue"],
```

- Sau khi khai báo, việc tiếp theo và gắn giá trị `modelValue` và emit event `update:modelValue` vào thẻ input trong Component Con:

```
<input
  type="text"
  :value="modelValue"
  @input="$emit('update:modelValue', $event.target.value)"
/>
```

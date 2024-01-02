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

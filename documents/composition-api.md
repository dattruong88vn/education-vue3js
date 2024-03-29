## COMPOSITION API

#### Định nghĩa

Composition API là một tính năng mới trong Vue 3, giúp chúng ta có thể viết component theo một cách khác, cụ thể ở đây là thẻ `script`.

Những video từ đầu đến giờ, chúng ta sử dụng `OPTIONS API`, bao gồm các thuộc tính nằm bên trong object được export defaut của thẻ `script` như: data(), computed, method, watchers, life cycle hook.

Sử dụng `Options API` là một cách để build Vue Component. Và một cách khác đó là sử dụng `Composition API`.

Khi build một Vue Component, bạn có thể lựa chọn 1 trong 2 cách trên đều được.

#### Lý do xuất hiện của Composition API

Có 2 lý do:

1. Nếu sử dụng `Options API`, khi Vue project được mở rộng và phát triển, sẽ trở nên rất khó quản lý và maintain.

Trong `Options API`, components được tổ chức theo các options trong export default object như data(), computed, methods, created, mounted. Mỗi options chứa các data hay logic của nhiều tính năng khác nhau.

Logic trong component không được gom nhóm theo feature, khiến cho code rất khó đọc khi component ngày càng lớn hơn (tương tự vấn đề trong React khi sử dụng Class Component, các feature phải sử dụng chung Life Cyclye Methods như `componentDidMount`, `componentDiđUpate`, `componentWillUnmount`...).

2. Việc tái sử dụng logic giữa các Component thực sự rất khó.

Mặc dù cả Vue 2 và Vue 3 đều cung cấp tính năng `Mixins` để thực hiện điều này nhưng nó có rất nhiều hạn chế.

Để khắc phục điều này, `Composition API` được giới thiệu trong Vue 3.

#### Replace Data Property

###### ref function

Vue Component có thể kết hợp giữa Options API và Composition API cùng lúc.

Trong thẻ script, import `ref` function từ `vue`. Function này khác với `template ref` dùng để tạo reference đến 1 thẻ HTML hoặc Component con.

Trong export default object, thêm vào function `setup`.

- Tạo một reactive reference: `const c_firstName = ref("Initial Name");`
- Để binding được data này vào thẻ template, cần return nó trong `setup` function:

```
setup() {
  const c_firstName = ref("Initial Name");

  return {
      c_firstName
  }
}
```

`c_firstName` không chỉ là 1 string, nó là một object có chứa key value. Trong `setup function`, hoàn toàn có thể update giá trị của nó (mutate) hoặc tạo ra một data mới (tương tự như computed trong option API).

```
setup() {
  const c_firstName = ref("Initial Name");
  c_firstName.value = "new name";

  const greet = `Hello ${c_firstName.value}`

  return {
      c_firstName,
      greet
  }
}
```

Khi hiển thị data từ Compotion API, trong `template` không cần trỏ đến value: `{{ c_firstName.value }}`. Vue sẽ tự unpack và hiển thị đúng value giúp chúng ta `{{ c_firstName }}`

###### reactive function

Khi sử dụng `ref()` để tạo các reactive refence, khi muốn update hoặc kết hợp nhiều data với nhau, chúng ta đều phải access đến key value trong mỗi object.

```
const greetHero = `Hello ${c_firstName.value} - ${c_lastName.value} a.k.a ${c_heroName.value}`;
```

Điều này khá bất tiện trong trường hợp có nhiều data và logic, việc lặp lại code này không tốt. Và đó là lý do tại sao cần `reactive function`.

Tương tự `ref`, import `reactive` function từ vue.

`Reactive` function nhận vào tham số là một object, mỗi key trong object này chính là một reactive data và return về chính object này.

```
import { reactive } from 'vue';

export default {
    setup() {
        const state = reactive({
            firstName: "Dat",
            lastName: "Truong",
            heroName: "Dat Crazy Dog"
        })
    }
}
```

Để binding các gía trị trả về từ `reactive`, cũng return về trong `setup function`.

###### So sánh ref và reactive function

1. Do `reactive` function chỉ tham số là object, nên khi data là các kiểu giá trị cơ bản như string, number, boolean và không liên quan nhau hoặc số lượng ít thì nên sử dụng `ref` .

Ví dụ cần lưu trữ trạng thái login:

- ref: const isLoggin = ref(false)
- reactive: const isLogginReactive = reactive({value: false}).

Có thể thấy, để access hoặc cập nhật giá trị loggin:

- ref: isLoggin.value
- reactive: isLogginReactive.value

2. Trường hợp có nhiều giá trị tương đồng hoặc có liên quan với nhau, chúng ta nên sử dụng `reactive` để gom nhóm các giá trị này vào chung 1 object.

Ví dụ: thay vì sử dụng `firstName`, `lastName` thành 2 biến riêng rẽ khi sử dụng, chúng ta có thể gom nhóm thành `profile` object.

```
const profile = reactive({
    firstName: "",
    lastName:""
})
```

#### Replace Computed Property

Để tạo ra data computed bằng `Composition API`, ta sử dụng method `computed` được import từ vue.

Method `computed` có đặc điểm:

- Return về giá trị cần computed, ta sẽ gán giá trị này vào 1 biến và export trong `setup()` function.
- Nhận vào 1 tham số là một function, gọi là callback. Callback function này trả về giá trị computed.

Ví dụ:

```
setup() {
    const fName = ref('');
    const lName = ref('');

    const fullName = computed(() => {
        return `${fName.value} ${lName.value}`
    })

    return {
        fName,
        lName,
        fullName
    }
}
```

#### Replace Watcher

Để `watch` một hoặc nhiều data khi làm việc với composition api, ta sử dụng function `watch` từ vue.

Function `watch` nhận vào 3 tham số:

- Thứ nhất: data cần watch. 1 data -> tên data, nhiều data -> Array, object (từ `reactive` function) hoặc một thuộc tính của object -> `getter function` return về data tương ứng, nếu là object thì phải là clone object (deep clone);
- Thứ hai: `callback function` được thực hiện khi data thay đổi. `Callback function` nhận vào 2 tham số là `newValue` và `oldValue`. Tuỳ thuộc vào tham số thứ nhất là theo dõi 1 hay nhiều data mà kiểu dữ liệu của `newValue` và `oldValue` là kiểu dữ liệu của data (trường hợp 1) hay là array (trường hợp nhiều)
- Thứ ba: `object` chứa các tuỳ chọn như `immediate` hay `deep`.

```
setup() {
    const firstName = ref("");
    const lastName = ref("");

    <!-- 1 data -->
    watch(firstName, (newValue, oldValue) => {
        <!-- Do something -->
    }, { immediate: true, deep: false})

    <!-- multidata -->
    watch([firstName, lastName], (newValues, oldValues) => {
        <!-- Do something -->
        console.log("Old First name: ", oldValues[0]);
        console.log("Old Last name: ", oldValues[1]);
        console.log("new First name: ", newValues[0]);
        console.log("new Last name: ", newValues[1]);
    })

    const state = reactive({
        reactiveFirstName: '',
        reactiveLastName: "",
        options: {
            heroName: ""
        }
    })

    <!-- object from reactive -->
    watch(() => { ...state }, (newVal, oldval) => {
        console.log("new": newVal);
        console.log("old": oldVal)
    })

    <!-- attribute of object -->
    watch(() => { ...state.options }, (newVal, oldval) => {
        console.log("new": newVal);
        console.log("old": oldVal)
    })
}
```

#### Replace Provide - Inject

###### Provide

Sử dụng `provide` function từ vue. Trong `setup()`, thực thi `provide` với 2 tham số `label` và `data`;

```
setup() {
    provide(key, value)
}
```

###### Inject

Sử dụng `inject` function từ vue. Trong `setup()` thực thi `inject` với 2 tham số: `label` và `default value` (cho trường hợp ko khai báo provide). Giá trị trả về chính là data từ provide.

```
setup() {
    const data = inject(key, defaultValue);
}
```

###### Lưu ý

Có thể sử dụng `Provide/Inject` cho:

- Static data
- Reactive data từ `ref` và `reactive` function.
- Method
- Computed

#### Life Cycle với composition API

Đối với `Options API`, mỗi `life cycle hook` là một options của object `export default`. Ngược lại, trong `composition API`, các life cycle hook là những function được import từ vue, và tên của các hook được thêm vào tiền tố `on_`.

Các function này đều nhận vào tham số là một callback function.

```
import {
    onBeforeMount,
    onMounted,
    onBeforeUpdate,
    onUpdated,
    onBeforeUnmount,
    onUnmounted
} from vue
```

2 hook có trong Options api là `beforeCreate` và `created` được lược bỏ trong Composition API. 2 hooks này được handle ngay bên trong `setup()` function.

#### Template Ref

Tạo template ref thông qua `ref` function, và return về trong `setup()` function.

```
<input type="text" ref="inputRef" />
...
const inputRef = ref(null);

return {
    inputRef
}
```

Để `focus` đến input element khi load page, sử dụng function `onMouted`.

```
onMounted(() => {
    inputRef.value.focus();
});
```

#### Props

Khai báo `props` tương tự như Options API.

Function `setup()` nhận vào tham số thứ nhất chính là `props object`.

```
setup(props) {
    const fullName = computed(() => {
        return `${props.firstName} + ${props.lastName}`
    })
}
```

#### Custom Event Component

Để emit một custom event trong Component Con, sử dụng tham số thứ 2 của `setup()` function, được gọi là `context`

Component Con

```
<button @click="handleEmit">Click</button>
...
setup(props, context) {

    function handleEmit() {
        context.emit(customEventName, params1, params2, ...);
    }

    return {
        handleEmit
    }
}
```

Component Cha

```
<ComponentCon @customEventName="doSomeThingFromCustomEvent" />
...

setup() {
    fucntion doSomeThingFromCustomEvent() {
        // do something ...
    }

    return {
        doSomeThingFromCustomEvent
    }
}
```

Object `context` chứa một số function hoặc object như `emit`, `slot`, `attrs`...

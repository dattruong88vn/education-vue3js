## Component

#### Giới thiệu chung

Vue cũng build UI dựa trên kiến trúc Component.

Có nghĩa là sẽ chia nhỏ UI thành nhiều thành phần khác nhau (mỗi thành phần là 1 component).

Mỗi vue application đều có một Root Component, được viết trong file `App.vue`, đây là Component gốc chưa tất cả những component khác như Header, Footer, Sidebar, MainContent.

#### Các thành phần của một component

Mỗi component được viết trong 1 file `.vue`, bao gồm 3 thành phần là `template`, `script` và `style`.

- `template`: hiển thị cấu trúc HTML
- `script`: logic của component
- `style`: style css của component

#### PROPS

```
// Parent Component
<template>
    <Greet name="Diana" hero-name="Wonder Woman" />
    <Greet :name="name" :hero-name="heroName" />
</template>

// Greet Component
<template>
  <div>
    <h2>Hello {{ name }} a.k.a {{ heroName }}</h2>
  </div>
</template>

<script>
export default {
  name: "greet-component",
  props: {
    name: String,
    heroName: String,
  },
};
</script>
```

Trong ví dụ trên, component Greet nhận vào 2 props là `name` và `hero-name`.

- Props name có thể truyền vào theo dạng `camelCase` hoặc `kebab-case`. Trong component Greet sẽ khai báo props về dạng `camelCase`.
- Mặc định props trong Vue sẽ chuyển primitive value về dạng `string`. Muốn pass props có kiểu `Number` hay `Boolean`, sử dụng `v-bind` directive

```
<Greet :age="35" :isOld="true"/>
```

###### Để khai báo giá trị mặc định của props, sử dụng object như sau:

```
...
export default {
    ...
    props: {
        age: {
            type: Number,
            default: 20,
        }
    }
}
...
```

Các thuộc tính của object:

- type: kiểu dữ liệu
- default: giá trị mặc định
- required: bắt buộc hay ko

###### `non-prop` attribute

Là một attribute được pass vào component, nhưng nó không match với bất cứ property nào được định nghĩa bên trong props option.

Ví dụ: `id`, `class`, `style`.

Mặc định khi thêm các attribute này, Vue sẽ tự động add vào root element của Component con, nếu trường hợp component con ko có element root, vue sẽ skip.

```
// Child Component with root element
<template>
    <div>
        ...
    </div>
</template>

// Child Component without root element
<template>
    <div>
        ...
    </div>
    <div>
        ...
    </div>
</template>


// Parent Componet
<template>
    <ChildComponent id="child-comp"/>
</template>
```

Để `non-prop` attribute thay vì apply vào root element mà apply vào một element bất kỳ bên trong root element,

- Thêm `v-bind="$attrs"` cho element mong muốn.
- Trong thẻ `script` -> `default export` -> thêm thuộc tính `inheritAttrs: false`

```
<template>
    <div>
        <div>
            ...
        </div>
        <div v-bind="$attrs">
            ...
        </div>
    </div>
</template>
```

###### Dynamic Component

Vue cung cấp một tính năng để có thể dynamic Component theo mong muốn.

Sử dụng thẻ `component` kèm thuộc tính `v-bind:is="<name-component>"`

```
<component :is="TabA"/>
```

###### Cache Dynamic Component

Đặt vấn đề:
sử dụng dynamic component để hiển thị dynamic content theo tab list.
Một hoặc nhiều content là form chứa thông tin user nhập vào.
Sau khi nhập thông tin và chuyển tab thì thông tin đã nhập sẽ bị mất.

Lý do:
Mỗi khi dynamic component thì Vue sẽ tạo ra một instance mới của component nên không cache lại được data trước đó.

Cách giải quyết:
Sử dụng thẻ `keep-alive` bọc bên ngoài thẻ `component` để vue cache lại tất cả dynamic component.

```
<keep-alive>
    <component :is="TabA" />
</keep-alive>
```

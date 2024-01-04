# Slots

#### Định nghĩa

`Slots` khá tương đồng với `children` trong React, với một số điểm như sau:

- Cho phép re-useable component bằng cách truyền vào component con các data khác nhau
- Khác với `props`, `slots` cho phép component cha có thể control được content bên trong component con.
- `slots` còn cho phép component cha nhúng bất cứ content nào vào component con bao gồm cả các thẻ HTML.

###### Cách thực hiện

Ở component cha, thay vì gọi component con bằng self-closing tag `<ConponentCon />` thay thế bằng cặp tag đóng mở `ComponentCon></ComponentCon>`.

Sau đó truyền bất cứ thẻ HTML mong muốn vào giữa 2 thẻ đóng mở.

Bên trong Component con, muốn nhậnd được content này chỉ cần khai báo cặp thẻ `<slot></slot>` bên trong `template` thì phần content được truyền vào sẽ thay thế thẻ `slot` này.

Trường hợp ở component cha ko truyền vào content, thì phần content bên trong thẻ `slot` sẽ được hiển thị.

Ví dụ:

```
// Cha
<ComponentCon>
    String Text
</ComponentCon>
<ComponentCon>
    <h2>String Text in H2 element</h2>
</ComponentCon>

// Con
<template>
    <div>
        <slot>Default Content</slot>
    </div>
</template>
```

#### Multiple slot

Component Cha có thể truyền nhiều content vào Component con tương ứng với nhiều slot khác nhau.

Để view có thể nhận biết được từng cặp `content-slot`, chúng ta thêm thuộc tính `name` vào thẻ slot `<slot name="card-header"></slot>.

Các thuộc tính `name` này phải unique và Vue cho phép 1 slot không cần đặt tên và nó sẽ được chọn làm slot mặc định.

```
<template>
    <div>
        // default slot
        <slot></slot>
    <div>
    <div>
        <slot name="name1"></slot>
    </div>
    <div>
        <slot name="name2"></slot>
    </div>
</template>
```

Trong component Cha, bên trong cặp thẻ opening-closing thay vì truyền một content như ở trên thì phải tách thành nhiều `template`, mỗi template sẽ chứa content tương ứng với từng `slot`.

Để connect template và slot, sử dụng `v-slot:<name-slot>`, đối với slot default thì cú pháp `v-slot:default`

```
<template>
    <ComponentCon>
        <template v-slot:default>
            Content Slot Default
        </template>
        <template v-slot:name1>
            Content Slot name 1
        </template>
        <template v-slot:name2>
            Content Slot name 2
        </template>
    </ComponentCon>

</template>
```

#### Slot Prop

Component Con có thể pass data đến component Cha thông qua `props` của slot. Từ đó Component Cha có thể quyết định content của Component con dựa vào data bên trong component con.

Ví dụ,

- Một component NameList hiển thị ra UI danh sách bao gồm firstName và lastName.
- Muốn hiển thị danh sách này ở một component khác với format chỉ bao gồm firstName.

###### Cách thực thiện

- Trong Component Con, sử dụng `v-bind:<prop-name>="<prop-value>"` để khai báo các prop muốn truyền ra ngoài theo slot

```
<slot :firstName="name.firstName" :lastName="name.lastName"></slot>
```

- Ở component cha, dùng cặp thẻ opening/closing để gọi component con. Bên trong cặp thẻ khai báo cặp thẻ `template` với thuộc tính `v-slot:<slot-name>='<slotProps>'` để chỉ định đến đúng slot tương ứng.
- `slotProps` là tên của object chứa toàn bộ props được truyền ra từ component con. Có thể đặt tên tuỳ thích
- Bên trong thẻ `template` tuỳ chỉnh content muốn hiển thị ở component con.

```
<ChildrenList>
    <template v-slot:default="slotProps">
        {{ slotProps.firstName }}
    </template>
</ChildrenList>
```

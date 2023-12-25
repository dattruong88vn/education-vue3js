## Modifier

#### Định nghĩa

- Là một suffix (hậu tố) có thể thêm vào trước `v-on` hoặc `v-model` để có thể thêm một số tính năng inline ngay trong template.
- Giúp chúng ta code cleaner hơn.

#### Một số modifier thông dụng

- v-model.trim: để trim text

```
<input id="name" type="text" v-model.trim="formValues.name" />
```

- v-model.number: chuyển giá trị từ kiểu string sang number (dùng cho cái field input, mặc định JS sẽ chuyển về string).

```
<input id="age" type="number" v-model.number="formValues.age" />
```

- v-model.lazy: cập nhật giá trị lazy, thay vì update data ngay khi user typing --> update sau khi user blur ra khỏi input. Giúp tăng performance khi không binding data từ template sau mỗi lần key press, thay vào đó binding khi blur khỏi input.

```
<input id="name" type="text" v-model.trim.lazy="formValues.name" />
```

###### Submit Modifiers

- @submit.prevent: thay thế cho event.preventDefault().

```
<form @submit.prevent="submitForm">
...
</form>
```

- Một số submit modifiers khác:
  - .stop: event's propagation
  - .self: chỉ trigger khi click vào chính element đó, click vào element con ko trigger
  - .once: chỉ trigger 1 lần
  - .passive:

###### Key press Modifiers

- @keyup.enter: thực thi function khi nhấn phím enter

```
<input type="number" v-model.number="formValues.age" @keyup.enter="submitForm"/>
```

- Một số modifier khác:
  @keyup: tab, escape, space, ctrl...

###### Mouse Click Modifiers

- @mouseclick: left, right, self...

## Conditional Rendering

Sử dụng các directive: `v-if`, `v-else`, `v-if-else`, `v-show`

#### v-if

```
<div v-if="number === 0">Render with v-if directive</div>
```

#### v-if and v-else

```
<h4 v-if="number2 === 0">v-if-else directive: number is zero</h4>
<h4 v-else>v-if-else directive: number is not zero</h4>
```

`v-else-if` và `v-else` bắt buộc phải đi ngay sau `v-if`.

#### Render multiple element with 1 condition

Sử dụng thẻ `template` để wrap nhiều element.

```
<template v-if="true">
    <h4>First</h4>
    <h4>Second</h4>
    <h4>Third</h4>
</template>
```

#### v-show

Rendering theo điều kiện tương tự như `v-if`.

Tuy nhiên khi điều kiện FALSE, `v-if` không add element vào DOM. Ngược lại `v-show` vẫn thêm element vào DOM kèm theo thuộc tính CSS `display: none`.

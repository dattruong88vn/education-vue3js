### .vue file

File có phần mở rộng `.vue` là một định dạng file có cấu trúc tương tự HTML để mô tả một phần của UI

Mỗi file .vue bao gồm 3 loại thẻ:

```
<template></template>
<script></script>
<style></style>
```

- template: tương tự HTML trên UI, xác định cấu trúc của DOM
- script: chứa logic và các chức năng
- style: chứa css của các thẻ html có trong template

Browser không thể hiểu được content trong file .vue, tuy nhiên nhờ vào webpack và các loader (trong đó có vue-loader) để có thể bundle từ vue file sang javascript file.

### Component

Trong vue, mỗi file .vue được xem là một Single File Component (SFC).

### Template syntax

Template block phụ trách phần markup (HTML).

Script block phụ trách phần logic của UI.

- Script block export default 1 object, object này có chứa một method data().
- Method data() return về một object, object này chứa toàn bộ data của component.
- Data này có thể sử dụng bên trong Template block.
- Đây được gọi là Declarative Programming (quan tâm input và output, ko quan tâm đến quá trình):
  - Chỉ cần cho Vue biết cách bind data vào HTML
  - Vue sẽ thực hiện phần còn lại

```
<script>
export default {
    name: "App",
    data() {
        return {
            name: "Thanh Dat"
        }
    }
}
</script>
```

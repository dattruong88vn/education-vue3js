## List Rendering

#### v-for directive

Sử dụng để duyệt:

- Array of String
- Array of Object
- Array of Array
- Block of HTML elements
- Key-value pairs of Object

Có thể sử dụng trên template tag.

###### Array of String

```
<h4 v-for="(name, index) in names" v-bind:key="name">{{ index }} {{ name }}</h4>
```

###### Array of Object

```
<h4 v-for="(fullName, index) in fullNames" :key="fullName.id">
    {{ index + 1 }} {{ fullName.fName }} - {{ fullName.lName }}
</h4>
```

###### Array of Array

```
<h4 v-for="actor in actors" :key="actor.id">
    <h6>{{ actor.name }}</h6>
    <span v-for="movie in actor.movies" :key="movie">{{ movie }}</span>
</h4>
```

###### Loop Object keys and values

```
<h4 v-for="(value, key, index) of myInfo" :key="key">
    {{ index + 1 }} {{ key }}:{{ value }}
</h4>
```

#### Key attribute

Vue khuyến cáo luôn phải cung cấp thêm thuộc tính `v-bind:key` đi kèm với `v-for` directive.

Key là unique được sử dụng để như một gợi ý cho Virtual DOM algorithm, nhằm so sánh sự khác biệt của DOM tree mới và DOM tree cũ.

Key attribute giúp cho Vue nhận biết được những items nào trong list có sự thay đổi, được thêm vào hoặc xoá đi, đóng vai trò quan trọng trong việc update UI chính xác và hiệu quả.

Không sử dụng key với `v-for` chỉ phù hợp khi list render không liên quan đến DOM state hoặc children component state.

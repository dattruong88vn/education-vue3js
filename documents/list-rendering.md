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

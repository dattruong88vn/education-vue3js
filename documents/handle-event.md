## Handle Event

#### Sử dụng `v-on:<event>` directive

```
// handle inline
<button v-on:click="count+=1">Increase 1</button>
<button v-on:click="count-=1">Decrease 1</button>

// handle through function
<button v-on:click="increase()">Increase 1</button>
<button v-on:click="decrease()">Decrease 1</button>
...

<script>
    export default {
        data() {
            return {
                count: 1
            }
        },
        methods: {
            increase() {
                this.count += 1;
            },
            decrease() {
                this.count -= 1;
            }
        }
    }
</script>
```

#### shorthand `@<event>`

```
// handle through function with shorthand syntax
<button @click="increase()">Increase 1</button>
<button @click="decrease()">Decrease 1</button>
...

<script>
    export default {
        data() {
            return {
                count: 1
            }
        },
        methods: {
            increase() {
                this.count += 1;
            },
            decrease() {
                this.count -= 1;
            }
        }
    }
</script>
```

#### Event object

Thêm vào một parameter `$event`, thì khi thực thi function có thể nhận được event object thông qua đối số `event`.

```
// event object with default parameter
<button @click="increase(1, $event)">Increase</button>
```

#### Thực thì nhiều method trong cùng 1 event

Sử dụng dấu `,` giữa các method.

```
<button @click="method1(), method2()">Click</button>
```

#### Không được handle event theo arrow function

```
// ERROR
<button @click="e => changeName(e)">Change name</button>
```

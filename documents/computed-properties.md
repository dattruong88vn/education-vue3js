## Computed Properties

###### Những cách hiển thị data ra UI:

    - Static HTML
    - Text interpolation
    - Simple Expressions
    - Methods
    - Computed Properties

#### Định nghĩa

Là những Properties có thể được bind vào template tương tự như data properties.

Được dùng để tạo ra các data mới từ những tài nguyên đã có sẵn.

Có tác dụng lớn đối với performance, khi nó được cached calculation và chỉ được update khi các dependencies của nó thay đổi (tương tự useMemo và useCallback trong React).

Mỗi property có thể được khai báo dưới 2 dạng:

- `function`: readonly
- `object`: có thể khai báo getter (read computed props) và setter (update computed props)

###### Cách khai báo: trong object `export default` của thẻ `<script`, thêm thuộc tính `computed` là một object.

Ví dụ:

```
export default {
  data() {
    return {
      lastName: "Truong Thanh",
      firstName: "Dat",
      items: [
        { id: 1, name: "TV", price: 100 },
        { id: 2, name: "Phone", price: 200 },
        { id: 3, name: "Laptop", price: 300 },
      ],
    };
  },
  methods: {
    addItem() {
      this.items.push({
        id: new Date(),
        name: "Appliance",
        price: Math.random() * 100,
      });
    },
  },
  computed: {
    fullName() {
      return this.lastName + this.firstName;
    },
    totalCost() {
      return this.items.reduce((sum, item) => {
        return (sum += item.price);
      }, 0);
    },
  },
};
```

#### So sánh Computed Property và Method

Mỗi khi dependencies trong Computed thay đổi, nó sẽ tính toán lại và update data, sau đó hiển thị lên UI.

Trường hợp có 1 event thay đổi dependency, nó sẽ chạy lại computed để update data. Câu hỏi đặt ra là cũng có thể sử dụng method để thực hiện chưc năng tương tự.

```
export default {
  data() {
    return {
      lastName: "Truong Thanh",
      firstName: "Dat",
      items: [
        { id: 1, name: "TV", price: 100 },
        { id: 2, name: "Phone", price: 200 },
        { id: 3, name: "Laptop", price: 300 },
      ],
    };
  },
  methods: {
    getTotal() {
      console.log("method getTotal");
      return this.items.reduce((sum, item) => {
        return (sum += item.price);
      }, 0);
    },
  },
  computed: {
    totalCost() {
      console.log("computed totalCost");
      return this.items.reduce((sum, item) => {
        return (sum += item.price);
      }, 0);
    },
  },
};
```

###### Vậy ưu điểm khi dùng computed ???

Ở ví dụ trên, nếu component được render lại do data thay đổi - như firstName hoặc lastName:

- Nếu sử dụng method `{{ getTotal() }}` thì nó vẫn thực thi và tính toán lại giá trị `total`.
- Nếu sử dụng computed, nó sẽ cache lại giá trị `total` trước đó và ko tính toán lại --> tối ưu performance.

###### Computed Props với getter và setter

- Khai báo computed dưới dạng `object` có chứa 2 method `get` và `set`.

- Method `get` tương tự như trường hợp khai báo computed dưới dạng function, return về data mong muốn.
- Method `set(value)` nhận vào value chính là fullName
  - Do fullName được tạo từ firstName và lastName nên cần cắt chuỗi và update 2 data này.

```
computed: {
    fullName: {
        get() {
            return this.lastName + this.firstName
        },
        set(value) {
            const names = value.split(" ");
            this.lastName = names[0];
            this.firstName = names[1];
        }
    }
},
```

- Tiếp theo, tạo 1 method để update computed fullName:

```
methods: {
    updateName() {
        this.fullName = "Some Text"
    }
}
```

- Cuối cùng chỉ cần thêm event để gọi đến method `updateName` là có thể `set` được data cho computed props.

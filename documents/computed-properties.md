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
Có tác dụng lớn đối với performance, khi nó được cached calculation và chỉ được update khi các dependencies của nó thay đổi (tương tự useMemo trong React).

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

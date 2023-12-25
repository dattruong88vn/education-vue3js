<template>
  <div>
    <h3>Fullname interpolation: {{ lastName }} {{ firstName }}</h3>
    <h3>Fullname computed: {{ fullName }}</h3>
    <h3>Fullname computed object: {{ name.fullName }}</h3>
    <button @click="lastName = 'Truong'">Change Name</button>
    <hr />
    <h3>
      Total cost:
      {{
        this.items.reduce((sum, item) => {
          return (sum += item.price);
        }, 0)
      }}
    </h3>
    <h3>Total cost computed: {{ totalCost }}</h3>
    <h3>Total cose method: {{ getTotal() }}</h3>
  </div>
  <hr />
  <button @click="addItem">Add Item</button>
</template>

<script>
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
    getTotal() {
      console.log("method getTotal");
      return this.items.reduce((sum, item) => {
        return (sum += item.price);
      }, 0);
    },
  },
  computed: {
    fullName() {
      return this.lastName + this.firstName;
    },
    name() {
      return {
        fullName: this.lastName + this.firstName,
      };
    },
    totalCost() {
      console.log("computed totalCost");
      return this.items.reduce((sum, item) => {
        return (sum += item.price);
      }, 0);
    },
  },
};
</script>

<style lang="scss" scoped></style>

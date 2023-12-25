<template>
  <div>
    <h3>Fullname interpolation: {{ lastName }} {{ firstName }}</h3>
    <h3>Fullname computed function: {{ fullName }}</h3>
    <button @click="lastName = 'Truong'">Change Name Static Text</button>
    <h3>Fullname computed object: {{ fullNameObject }}</h3>
    <button @click="changeFullNameSetterComputed">
      Change name through set function
    </button>
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
  <br />
  <hr />
  <div>
    <h4>Conditional Rendering List with v-for and v-if</h4>
    <div v-for="item in items" :key="item.id">
      <span v-if="item.price > 100"> {{ item.name }} - {{ item.price }} </span>
    </div>
    <hr />
    <h4>Conditional Rendering List with Computed Properties</h4>
    <div v-for="item in expensiveItems" :key="item.id">
      {{ item.name }} - {{ item.price }}
    </div>
  </div>
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
    changeFullNameSetterComputed() {
      this.fullNameObject = "Dat 09";
    },
  },
  computed: {
    fullName() {
      return this.lastName + " " + this.firstName;
    },
    fullNameObject: {
      get() {
        return this.lastName + " " + this.firstName;
      },
      set(value) {
        // fullName is combined from lastName and firstName
        // split value and assign to lastName and firstName
        const names = value.split(" ");
        this.lastName = names[0];
        this.firstName = names[1];
      },
    },
    totalCost() {
      console.log("computed totalCost");
      return this.items.reduce((sum, item) => {
        return (sum += item.price);
      }, 0);
    },
    expensiveItems() {
      return this.items.filter((item) => item.price > 100);
    },
  },
};
</script>

<style lang="scss" scoped></style>

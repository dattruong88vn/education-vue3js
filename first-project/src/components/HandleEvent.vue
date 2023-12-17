<template>
  <h1>Handle Event</h1>
  <div>
    <h2>{{ name }}</h2>
    <div>
      <button type="button" v-on:click="name = 'The Flash'">
        Change Name Click from View
      </button>
    </div>
    <div>
      <button
        type="button"
        v-on:click="changeName($event), increase(1, $event)"
      >
        Change Name Click By Method
      </button>
    </div>
    <div>
      <button type="button" v-on:mouseover="changeName($event)">
        Change Name Mouse Over By Method
      </button>
    </div>
  </div>
  <div>
    <h2>{{ count }}</h2>
    <div>
      <button v-on:click="decrease(1, $event)">Decrease 1</button>
      <button v-on:click="increase(1)">Increase 1</button>
      <button v-on:click="decrease(5, $dat)">Decrease 5</button>
      <button v-on:click="increase(5)">Increase 5</button>
      <button @click="decrease(10)">Decrease 10 (shorthand)</button>
      <button @click="increase(10)">Increase 10 (shorthand)</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Thanh Dat",
      count: 1,
    };
  },
  methods: {
    changeName(event) {
      this.name += "Batman";
      console.log(event);
    },
    decrease(num, event) {
      console.log(event);
      this.count -= num;
    },
    increase(num) {
      this.count += num;
    },
  },
};
</script>

<style lang="scss" scoped></style>

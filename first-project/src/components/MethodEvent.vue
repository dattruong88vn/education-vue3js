<template>
  <h1>Methods</h1>
  <div>
    <h2>Sum method: {{ sum(1, 2, 3) }}</h2>
    <h2>Multiply method: {{ multiply(7) }}</h2>
    <h2>Multiply method with data attribute: {{ multiply(baseValue) }}</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      number: 7,
      baseValue: 9,
    };
  },
  methods: {
    sum(a, b, c) {
      return a + b + c;
    },
    multiply(num) {
      return num * this.number;
    },
  },
};
</script>

<style lang="scss" scoped></style>

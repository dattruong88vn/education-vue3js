<template>
  <h1>Conditional Rendering</h1>
  <div>
    <h4 v-if="number === 0">v-if directive: number is zero</h4>
  </div>
  <div>
    <h4 v-if="number2 === 0">v-if and v-else directive: number is zero</h4>
    <h4 v-else>v-if and v-else directive: number is not zero</h4>
  </div>
  <div>
    <h4 v-if="number3 === 0">v-else-if: number is zero</h4>
    <h4 v-else-if="number3 > 0">v-else-if: number is more than zero</h4>
    <h4 v-else-if="number3 < 0">v-else-if: number is less than zero</h4>
    <h4 v-else>v-else-if: not a number</h4>
  </div>

  <template v-if="display">
    <h4>First</h4>
    <h4>Second</h4>
    <h4>Third</h4>
  </template>

  <div>
    <h2>Compare v-if and v-show</h2>
    <div v-if="display">v-if</div>
    <div v-show="display">v-show</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      number: 0,
      number2: 5,
      number3: -5,
      display: false,
    };
  },
};
</script>

<style></style>

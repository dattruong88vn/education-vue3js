<template>
  <div>
    <button @click="increaseCount">Click {{ count }} times</button>
  </div>
</template>

<script>
import useCounter from "../hooks/useCounter";

export default {
  name: "Click-Count",
  setup() {
    const { count, increaseCount } = useCounter(10, 5);

    return {
      count,
      increaseCount,
    };
  },
};
</script>

<style scoped></style>

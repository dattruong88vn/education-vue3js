<template>
  <div>
    <div @mouseover="increaseCount">Click {{ count }} times</div>
  </div>
</template>

<script>
import useCounter from "../hooks/useCounter";

export default {
  name: "Click-Count",
  setup() {
    const { count, increaseCount } = useCounter();

    return {
      count,
      increaseCount,
    };
  },
};
</script>

<style scoped></style>

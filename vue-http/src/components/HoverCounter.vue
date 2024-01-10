<template>
  <div>
    <h3 @mouseover="increaseCount">Hover to increase count {{ count }}</h3>
  </div>
</template>

<script>
import CounterMixin from "../mixins/counter";

export default {
  name: "HoverCounter",
  mixins: [CounterMixin],
};
</script>

<style scoped></style>

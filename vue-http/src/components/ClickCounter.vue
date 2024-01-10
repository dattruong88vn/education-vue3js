<template>
  <div>
    <button @click="increaseCount">{{ count }}</button>
  </div>
</template>

<script>
import CounterMixin from "../mixins/counter";

export default {
  name: "ClickCounter",
  mixins: [CounterMixin],
};
</script>

<style scoped></style>

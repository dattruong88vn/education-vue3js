<template>
  <div>Composition Prop computed: Hello {{ cFullName }}</div>
</template>

<script>
import { computed } from "vue";

export default {
  name: "Person-Child",
  props: {
    firstName: {
      type: String,
    },
    lastName: {
      type: String,
    },
  },
  setup(props) {
    const cFullName = computed(() => {
      return `${props.firstName} ${props.lastName}`;
    });

    return {
      cFullName,
    };
  },
};
</script>

<style scoped></style>

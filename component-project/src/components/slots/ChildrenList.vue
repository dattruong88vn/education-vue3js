<template>
  <div>
    <h4 v-for="name in names" :key="name.firstName">
      <slot :firstName="name.firstName" :lastName="name.lastName"></slot>
    </h4>
  </div>
</template>

<script>
export default {
  name: "children-list",
  data() {
    return {
      names: [
        { firstName: "Batman", lastName: "Bruce Wayne" },
        { firstName: "Superman", lastName: "Clark Ken" },
        { firstName: "The Flash", lastName: "Barry Allen" },
      ],
    };
  },
};
</script>

<style scoped></style>

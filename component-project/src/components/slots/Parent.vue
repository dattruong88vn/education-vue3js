<template>
  <Children>
    <template v-slot:header> Header </template>
    <template v-slot:default>
      <img src="https://picsum.photos/200" />
    </template>
    <template v-slot:footer> Footer </template>
  </Children>

  <hr />

  <ChildrenList>
    <template v-slot:default="slotProps">
      {{ slotProps.firstName }}
    </template>
  </ChildrenList>

  <ChildrenList>
    <template v-slot:default="slotProps">
      {{ slotProps.firstName }} - {{ slotProps.lastName }}
    </template>
  </ChildrenList>
</template>

<script>
import Children from "./Children.vue";
import ChildrenList from "./ChildrenList.vue";
export default {
  name: "slot-parent",
  components: {
    Children,
    ChildrenList,
  },
};
</script>

<style scoped></style>

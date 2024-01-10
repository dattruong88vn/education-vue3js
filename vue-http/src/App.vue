<template>
  <PostList />
  <Parent />
</template>

<script>
import PostList from "./components/PostList.vue";
import Parent from "./components/Parent.vue";

export default {
  name: "App",
  components: {
    Parent,
    PostList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
  <!-- <button @click="getPosts">Load posts</button> -->
  <h3 v-if="errorMessage">{{ errorMessage }}</h3>
  <div v-for="post in posts" :key="post.id">
    <h3>{{ post.id }}. {{ post.title }}</h3>
    <p>{{ post.body }}</p>
    <br />
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "PostList",
  data() {
    return {
      posts: [],
      errorMessage: "",
    };
  },
  methods: {
    async getPosts() {
      try {
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts"
        );
        this.posts = response.data;
      } catch (error) {
        console.log(error);
        this.errorMessage = "Something went wrong";
      }
    },
  },
  created() {
    this.getPosts();
  },
};
</script>

<style scoped></style>

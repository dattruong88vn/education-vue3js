<template>
  <div>
    <form @submit.prevent="createPost">
      <div>
        <label for="userId">Post User Id</label>
        <input name="userId" v-model="formData.userId" />
      </div>
      <div>
        <label for="title">Post Title</label>
        <input name="title" v-model="formData.title" />
      </div>
      <div>
        <label for="body">Post Body</label>
        <input name="body" v-model="formData.body" />
      </div>
      <button>Create Post</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "CreatePost",
  data() {
    return {
      formData: {
        userId: "",
        title: "",
        body: "",
      },
    };
  },
  methods: {
    async createPost() {
      try {
        const response = await axios.post(
          "https://jsonplaceholder.typicode.com/posts",
          this.formData
        );
        console.log({ response });
      } catch (err) {
        console.log({ err });
      }
    },
  },
};
</script>

<style scoped></style>

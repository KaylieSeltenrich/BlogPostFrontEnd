<template>
  <div>
    <p>Blog Content:</p>
    <textarea v-model="content" placeholder="500 characters max"></textarea>
    <br />
    <p>Enter your name:</p>
    <input type="text" v-model="created_by" /> <br/>
    <button @click="createBlogPost()"> Create Post </button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      content: "",
      created_by: "",
    };
  },
  methods: {
    createBlogPost: function () {
      axios
        .request({
          url: "http://127.0.0.1:5000/blog",
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          data: {
            content: this.content,
            created_by: this.created_by,
          },
        })
        .then((response) => {
          console.log(response);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style scoped>
</style>
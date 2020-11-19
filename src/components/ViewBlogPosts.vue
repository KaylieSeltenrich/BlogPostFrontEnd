<template>
  <div>
    <div v-for="post in posts" :key="post[0]">
      <h2>{{'"' + post[0] + '"' }}</h2>
      <p>{{ post[1] }}</p>
      <p> Created By: </p>
      <h4>{{ post[2] }}</h4>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "ViewTodoItems",
  mounted() {
    this.getAllPosts();
  },
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    getAllPosts: function () {
      axios
        .request({
          url: "http://127.0.0.1:5000/blog",
          method: "GET",
        })
        .then((response) => {
          console.log(response);
          this.posts = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
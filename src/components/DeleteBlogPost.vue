<template>
  <div>
    <button @click="deleteBlogPost()">Delete Post</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "DeleteBlogPost",

  props: {
    blogpost_id: {
      type: Number,
      required: true,
    },
  },

  methods: {
    deleteBlogPost: function () {
      axios
        .request({
          url: "http://127.0.0.1:5000/blog",
          method: "DELETE",
          headers: {
            "Content-Type": "application/json",
          },
          data: {
            id: this.blogpost_id,
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
div {
  margin: 5px;
}
</style>
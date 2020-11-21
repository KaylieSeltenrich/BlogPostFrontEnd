<template>
  <div>
    <h1>Blog Content:</h1>
    <textarea v-model="content" placeholder="500 characters max"></textarea>
    <br />
    <p>Enter your name:</p>
    <input type="text" v-model="created_by" placeholder="20 characters max" /> <br />
    <button @click="createBlogPost()">Create Post</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "CreateBlogPost",

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
          url: "http://kayliesblogsite.ml/api/blog",
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
button {
  margin: 15px;
  font-size: 1em;
  font-weight: bold;
}

textarea {
  height: 20vh;
  width: 65vw;
  padding: 20px;
  font-size: 1.2em;
}

input {
 height: 3vh;
 width: 20vw;
 padding: 5px;
 font-size: 1em;
}
</style>
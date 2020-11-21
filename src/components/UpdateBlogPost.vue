<template>
  <div>
    <p>Update Content:</p>
    <textarea v-model="content" placeholder="500 characters max"></textarea>
    <br />
    <p>Update name:</p>
    <input type="text" v-model="created_by" placeholder="20 characters max" /> <br />
    <button @click="updateBlogPost()">Update Post</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "UpdateBlogPost",
  data() {
    return {
      content: "",
      created_by: "",
    };
  },

  props: {
    blogpost_id: {
      type: Number,
      required: true,
    },
  },

  methods: {
    updateBlogPost: function () {
      axios
        .request({
          url: "http://kayliesblogsite.ml/api/blog",
          method: "PATCH",
          headers: {
            "Content-Type": "application/json",
          },
          data: {
            content: this.content,
            created_by: this.created_by,
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
button {
  margin: 10px;
}

textarea {
  height: 5vh;
  width: 30vw;
}
</style>
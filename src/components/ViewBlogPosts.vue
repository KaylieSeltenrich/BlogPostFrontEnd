<template>
  <div class="page-container">
    <div class="post-container" v-for="post in posts" :key="post[0]">
      <h2>{{ '"' + post[0] + '"' }}</h2>
      <p> <b>Created By:</b> {{ post[2] }} </p>
      <p> <b>Time Created:</b> {{ post[1] }} </p>
      <update-blog-post :blogpost_id="post[3]"> </update-blog-post>
      <delete-blog-post :blogpost_id="post[3]"> </delete-blog-post>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import UpdateBlogPost from "./UpdateBlogPost.vue";
import DeleteBlogPost from "./DeleteBlogPost.vue";

export default {
  name: "ViewBlogPosts",
  components: {
    UpdateBlogPost,
    DeleteBlogPost
  },
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

<style lang="css" scoped>
.page-container{
  display: grid;
  grid-template-columns: 1fr 1fr;
  width: 90%;
  margin: 5%;

}
.post-container {
border: 1px solid black;
padding: 2vh;
margin: 10px;

}
</style>
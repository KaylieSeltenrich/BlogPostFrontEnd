<template>
  <div id="app">
  <create-blog-post> </create-blog-post>
  <view-blog-posts> </view-blog-posts>

  </div>
</template>

<script>
import ViewBlogPosts from "./components/ViewBlogPosts.vue";
import CreateBlogPost from "./components/CreateBlogPost.vue";

export default {
  name: 'App',
  components: {
    ViewBlogPosts,
    CreateBlogPost,
  }
}
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

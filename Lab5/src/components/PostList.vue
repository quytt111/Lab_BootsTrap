<template>
    <div>
      <h2>Danh sách bài viết</h2>
      <div v-for="(post, index) in posts" :key="index" :class="{'high-lighted': post.tieuDe.length > 20}"
        :style="{backgroundColor: post.backgroundColor, color: post.textColor}" class="post">
        <h3>{{ post.tieuDe }}</h3>
        <h4>{{ post.tenTG }}</h4>
        <p>{{ post.noiDung }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
      name: "PostList",
      props: {
          posts: {
              type: Array,
              required: true
          }
      }
  };
</script>
  
  <style>
  .post {
    padding: 20px;
    margin: 10px 0;
    border: 1px solid white;
    border-radius: 10px;
  }
  .highlighted {
    border: 2px solid lightgray;
  }
  </style>
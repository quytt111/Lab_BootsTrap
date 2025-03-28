<script setup>
import { ref } from "vue";
import Baii_Lab5 from "./components/Bai1_Lab5.vue";
import Bai2_Lab5 from "./components/Bai2_Lab5.vue";
import Bai3_Lab5 from "./components/Bai3_Lab5.vue";
  import CreatePost from './components/CreatePost.vue';
  import PostList from './components/PostList.vue';

  const posts = ref([]);

  function addPost(post){
    posts.value.push(post);
  }
</script>

<template>
  <!-- <div>
    <h1>Bài 1: Sử dụng sự kiện và binding động</h1>
    <Baii_Lab5></Baii_Lab5>
    <br />
    <hr />
    <h1>Bài 2: sử dụng tow-way binding và v-model và sử dụng API cơ bản</h1>
    <Bai2_Lab5></Bai2_Lab5>
    <br />
    <hr />
    <h1>Bài 3: sử dụng reactive để tạo 1 đối tượng thongTin</h1>
    <Bai3_Lab5></Bai3_Lab5>
  </div> -->
  <div id="app">
        <h1>Blog nhỏ với vue.js</h1> 
        <CreatePost @add-post="addPost"/> 
        <PostList :posts="posts"/> 
  </div>
</template>

<style>
        #app{
                max-width: 800px;
                margin: 0 auto;
                padding: 20px;
        }
</style>

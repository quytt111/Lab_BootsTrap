<script setup>
import { ref } from 'vue';
import Bai1_Lab7 from './components/Bai1_Lab7.vue';
import Bai2_Lab7 from './components/Bai2_Lab7.vue';

import CommentComponent from './components/CommentComponent.vue';
import LoginComponent from './components/LoginComponent.vue';

const isLoggedin = ref(false);
const nguoiDungDangNhap = ref('');

function dangNhapThanhCong(email) {
  isLoggedin.value = true; // Đặt thành true khi đăng nhập thành công
  nguoiDungDangNhap.value = email; // Lưu email của người dùng
}
</script>

<template>
  <div class="row container">
    <div class="col-sm-8">
    <LoginComponent v-if="!isLoggedin" @Loggedin="dangNhapThanhCong"></LoginComponent>
  </div>
  <div class="col-sm-4">
    <CommentComponent :email="nguoiDungDangNhap"></CommentComponent>
  </div>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

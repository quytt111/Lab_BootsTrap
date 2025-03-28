<template>
    <div>
      <h1>Tạo bài viết mới</h1>
      <input type="text" v-model="tieuDe" placeholder="Tiêu đề bài viết"> <!-- Thêm v-model để liên kết với post.tieuDe -->
      <input type="text" v-model="tenTG" placeholder="Tên Tác Giả"> <!-- Thêm v-model để liên kết với post.tenTG -->
      <textarea v-model="noiDung" placeholder="Nội dung bài viết"></textarea> <!-- Thêm v-model để liên kết với post.noiDung -->
      <button @click="dangBai">Đăng bài</button> <!-- Thêm sự kiện click để gọi hàm dangBai -->
    </div>
  </template>
  
  <script setup>
  import {ref} from 'vue';

  const emit = defineEmits(['add-post']);

  const tieuDe = ref('');
  const tenTG = ref('');
  const noiDung = ref('');

  function dangBai(){
      if(tieuDe.value && tenTG.value && noiDung.value){
          const newPost = {
            tieuDe: tieuDe.value,
              tenTG: tenTG.value,
              noiDung: noiDung.value
          };

          emit('add-post',newPost);

          tieuDe.value = '';
          tenTG.value = '';
          noiDung.value = '';
      }
  }
</script>
  
  <style>
  input,
  textarea {
    display: block;
    width: 100%;
    margin: 10px 0;
    padding: 10px 20px;
    border-radius: 5px;
    border: 1px solid #ccc; /* Sửa màu border cho rõ ràng hơn */
  }
  button {
    padding: 10px 20px;
    background-color: blue;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  </style>
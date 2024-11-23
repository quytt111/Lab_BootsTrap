<template>
    <div>
      <h1>Nhập tháng đi bạn: </h1>
      <input type="number" v-model="now" min="0" max="12" >
      <p v-if="now >= 13 || now < 1">Không tìm thấy tháng <strong style="color: red;">{{ now }}</strong> </p>
      <p v-else-if="now >= 1 && now <= 3">Mùa Xuân</p>
      <p v-else-if="now >= 6">Mùa Hè</p>
      <p v-else-if="now <= 9">Trung Thu</p>
      <p v-else>Mùa đông</p>
  </div>
    
  </template>
  
  <script setup>
      import {ref} from 'vue'
      const now = ref(new Date().getMonth() + 1);

  </script>
  
  <style>
  
  </style>
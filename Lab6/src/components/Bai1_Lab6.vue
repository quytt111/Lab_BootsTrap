<template>
  <div>
    <h1>Nhập điểm đi bạn: </h1>
    <input type="number" v-model="diem" min="0" max="10">
    <p v-if="diem >= 11">10đ là tối đa xin nhập lại</p>
    <p v-else-if="diem >= 9">Xuất sắc</p>
    <p v-else-if="diem >= 8">Giỏi</p>
    <p v-else-if="diem >= 6.5">Khá</p>
    <p v-else-if="diem >= 5">Trung bình</p>
    <p v-else>Yếu</p>
</div>
  
</template>

<script setup>
    import {ref} from 'vue'
    const diem = ref(0);
</script>

<style>

</style>
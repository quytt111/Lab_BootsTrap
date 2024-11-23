<template>
  <div class="container">
    <h3 class="mt-3">Bình luận bài viết</h3>
    <div class="card">
      <img class="card-img" src="../assets/images/eat-clean.png" alt="" />
      <h3 class="mt-2 ms-3 me-3">8 loại rau củ quả giàu canxi</h3>
      <p class="mt-2 ms-3 me-3">
        Canxi là khoáng chất cần thiết đối với cơ thể người. Có nhiều cách để bổ
        sung canxi...
      </p>
    </div>
    <br />
    <form @submit.prevent="goiBinhLuan">
      <h4 class="mb-3">Bình luận bài viết tại đây</h4>
      <textarea v-model="binhLuan" class="border border-1 rounded-2 w-100" placeholder="Nhập bình luận..."></textarea>
      <button type="submit" class="bg-success p-2 rounded-2 text-light border-0">Gởi Bình luận</button>
    </form>
    <h5 class="mt-3">Danh sách các bình luận:</h5>
    <div>
      <ul class="mt-3">
        <li v-for="(binhLuanItem, index) in binhLuans" :key="index">
          <b>{{ binhLuanItem.name }}:</b> {{ binhLuanItem.Text }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const props = defineProps(['email']);

const binhLuan = ref('');
const binhLuans = ref([]);

const goiBinhLuan = () => {
  if (binhLuan.value) {
    binhLuans.value.push({
      name: props.email || 'Người dùng ẩn danh',
      Text: binhLuan.value
    });
    binhLuan.value = '';
  }
}
</script>
  
<style>
.card-img {
  width: 100%;
  height: 200px;
  object-fit: cover;
}
</style>

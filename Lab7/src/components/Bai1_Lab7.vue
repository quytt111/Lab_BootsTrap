<template>
  <div class="p-5 col-sm-2">
    <form @submit.prevent="themCongViet" action="">
    <label  class="text-muted"> Tên Công việc: </label>
    <br>
    <input v-model="congVietN.ten" class="form-control" type="text">
    <br>
    <button class="btn btn-info">Thêm công việt</button>
    </form>
    <ul class="list-group mt-4" >
      <li class="list-group-item d-flex justify-content-between align-items-center" v-for="job in congViet" :key="job.id">{{ job.ten }}
        <button class="btn btn-danger btn-sm" @click="xoa(job.id)">Xóa</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
  import {ref} from 'vue';
  const congViet= ref ([
    {
      id: 1,
      ten: 'Ăn Sáng',
    },
    {
      id: 2,
      ten: 'Đi học',
    },
    {
      id: 3,
      ten: 'Chơi bóng rổ',
    }
  ])
  const xoa = (id) => {
    congViet.value= congViet.value.filter((job) => job.id != id)
  }
  const congVietN = ref({
    ten: "",
  })
  const themCongViet = () => {
    if(!congVietN.value.ten){
      errorMessage.value =
      "Vui lòng công việc";
    }
    congViet.value.push({
      id: Date.now(),
      ten: congVietN.value.ten
    })
    congVietN.value = {ten: ''}
  }
</script>

<style>

</style>
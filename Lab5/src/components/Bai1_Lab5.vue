<template>
  <div >
    <p > {{ thongDiep }}</p>
    <button class="btn btn-dark" @click="capNhatThongDiep">
        Nhấn để thay đổi
    </button>
  </div>
</template>

<script>
import {ref} from 'vue';

export default {
  data() {
    const thongDiep = ref('Thông điệp ban đầu');
    
    const capNhatThongDiep = () => {
      thongDiep.value = 'Thông điệp được thay đổi';
    };

    return {
      thongDiep,
      capNhatThongDiep
    };
  }
};
</script>

<style>

</style>
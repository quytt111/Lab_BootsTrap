<template>
  <div>
    <button @click="hien">Ẩn/Hiện</button>
    <p v-show="isAnHien">Nhấn để hiện thêm....</p>
  </div>
</template>

<script>
import {ref} from 'vue'
export default {
    setup(){
        const isAnHien = ref(false);
        const hien = () => {
            isAnHien.value = !isAnHien.value;
        }
    return {
        isAnHien,
        hien
    }
    },
    
}
</script>

<style>

</style>
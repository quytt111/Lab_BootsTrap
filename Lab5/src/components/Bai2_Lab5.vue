<template>
  <div>
    <input type="text" v-model="nhap" placeholder="Nhập dữ liệu của bạn ở đây">
    <p>Dữ liệu của bạn: {{ nhap }} </p>
  </div>
</template>

<script>
import {ref} from 'vue';

export default {
    data(){
        const nhap = ref('');
    
    return{
        nhap,
    };
}
};    
</script>

<style>

</style>
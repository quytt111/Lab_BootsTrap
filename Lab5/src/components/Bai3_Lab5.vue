<template>
    <div>
        <div >
        <label for="">Họ và tên</label>
        <input type="text" v-model="thongTin.name">
        <br>
        <label for="">Tuổi</label>
        <input type="number" v-model="thongTin.age">
        <br>
        <label for="">Email</label>
        <input type="text" v-model.lazy="thongTin.email">
        </div>
        <div class="bg-light">
            <h1>Thông tin vừa nhập: </h1>
            <p><strong>Họ và Tên: </strong> {{ thongTin.name }}</p>
            <p><strong>Tuổi: </strong> {{ thongTin.age }}</p>
            <p><strong>Email: </strong> {{ thongTin.email }}</p>
        </div>
    </div>

</template>

<script>
import { reactive } from 'vue';
export default {
    setup(){
        const thongTin = reactive({
            name: '',
            age: '',
            email: ''
        });
        return{
            thongTin
        }
    }
}
</script>

<style>

</style>
<template>
    
         <h1>{{ greeting }}</h1>
        <button v-bind:title="button" @click="Change">click me</button>
    
</template>
<script>
    export default{
        data(){
            return{
            greeting: 'Xin chào bạn!',
            button: 'Nhấn để thay đổi'
        };
    },
    methods:{
        Change(){
            this.greeting = 'Hello, World';
            this.button = 'Lời chào mới được cập nhật';
        }
    }
}
</script>
<style>
</style>
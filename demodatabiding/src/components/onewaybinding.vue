<template>
<div>
    <!-- Tên trang web bạn muốn đến<input type="text" v-bind:value="name"> -->
    Tên trang web bạn muốn đến<input type="text" :value="name">
    <br>
    <a class="btn" :href="url">đi đến trang</a>
</div>
<!-- two way binding  -->
<div>
    Họ và tên của bạn {{ name }}
    <br>
    <input type="text" v-model="name">
    <p>Tuổi của bạn là: {{ age }}</p>
    <input type="number" v-model="age">
    <p>Giới Tính của bạn: {{ GioiTinh }}</p>
    <input type="radio" v-model="GioiTinh" value="Nam">Nam
    <input type="radio" v-model="GioiTinh" value="Nữ">Nữ
    <br>
    <p>Quốc gia của bạn là: {{ QuocTich.join( ', ' ) }}</p>
    <select v-model="QuocTich" multiple>
        <option value="Việt Nam">Việt Nam</option>
        <option value="Lào">Lào</option>
        <option value="Campuchia">Campuchia</option>
    </select>
    <p>Quốc gia của bạn là: {{ QuocTich.join( ', ' ) }}</p>
    <select v-model="QuocTich" >
        <option value="Việt Nam" >Việt Nam</option>
        <option value="Lào">Lào</option>
        <option value="Campuchia">Campuchia</option>
    </select>
    <br>
    <p>Sở thích của bạn: {{ soThich.join(', ') }}</p>
    <input type="checkbox" value="Bóng đá" v-model="soThich"> Bóng đá
    <input type="checkbox" value="Bi da"v-model="soThich"> Bi Da
    <input type="checkbox" value="Du Lịch"v-model="soThich"> Du Lịch
</div>
</template>

<script>
    export default{
        data(){
            return{
                name: 'FPT',
                age: '',
                GioiTinh: '',
                QuocTich: [],
                soThich: [],
                url: 'https://fptplay.vn/'
            }
        }
    }

</script>
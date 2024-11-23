<template>
    <div class="container mt-5">
      <h1 class="text-center">Kiến thức sức khỏe cộng đồng</h1>
      <div class="row">
        <div class="col-sm-4" v-for="baiViet in baiBiet" :key="baiViet.id">
          <div class="card custom-card">
            <img :src="baiViet.hinhAnh" alt="Hình ảnh" class="card-img-top" />
            <div class="card-body d-flex flex-column">
              <h3 class="card-title">{{ baiViet.tieuDe }}</h3>
              <p class="card-text flex-grow-1">{{ baiViet.noiDung }}</p>
              <button class="btn btn-info mt-auto w-100" @click="Change1">Xem chi tiết</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import img1 from '../assets/images/banner1.jpg';
  import img2 from '../assets/images/banner2.jpg';
  import img3 from '../assets/images/banner3.jpg';
  
  const baiBiet = ref([
    {
      id: 1,
      tieuDe: '8 loại rau củ quả giàu canxi',
      noiDung: 'Canxi là khoáng chất cần thiết đối với cơ thể người. Có nhiều cách để bổ sung canxi, trong đó bổ sung qua đường ăn uống là cách tốt nhất. Có 8 loại rau củ giàu canxi....',
      hinhAnh: img1,
    },
    {
      id: 2,
      tieuDe: 'Các loại gia vị tốt cho sức khỏe',
      noiDung: 'Một số loại gia vị cung cấp nhiều polyphenol chống oxy hóa cao hơn các loại gia vị quen thuốc khác, với một lượng nhỏ các món ăn đã thêm hương thơm và vị hấp dẫn....',
      hinhAnh: img2,
    },
    {
      id: 3,
      tieuDe: '9 loại đậu bổ dưỡng nên dùng nhiều',
      noiDung: 'Đậu lăng, đậu nành, đậu phộng, đậu Hà Lan giàu chất xơ, protein cùng nhiều vitamin và khoáng chất giúp giảm lượng đường trong máu, tốt cho tim....',
      hinhAnh: img3,
    },
  ]);
  </script>
  
  <style scoped>
  .custom-card {
    height: 400px;            /* Chiều cao cố định */

  }
  
  .card-img-top {
    height: 200px;            /* Chiều cao cố định cho hình ảnh */
    object-fit: cover;        /* Cắt hình ảnh theo khung mà không bị méo */
  }
  

  
  .card-title {
    font-size: 1.2rem;
    font-weight: bold;
  }
  

  </style>
  
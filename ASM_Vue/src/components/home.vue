<template>
  <div id="app">
    <nav class="bg-light navbar navbar-expand-lg navbar-light p-2 shadow-sm fixed-top">
      <div class="container-xxl">
        <a class="navbar-brand" href="#">
          <img src="#" alt="Logo" style="width: 150px;" />
        </a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#Cainut">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="Cainut">
          <ul class="navbar-nav nav-underline me-auto">
            <li><a class="nav-link text-dark" href="#"><i class="fa-solid fa-list"></i> Bài viết</a></li>
            <li><a class="nav-link text-dark " href="#"><i class="fa-solid fa-film"></i> nổi bật</a></li>
            <li><a class="nav-link text-dark " href="#"><i class="fa-solid fa-info"></i> Giới thiệu</a></li>
            <li><a class="nav-link text-dark" href="#"><i class="fa-solid fa-calendar"></i> Hổ trợ</a></li>
          </ul>
          <ul class="navbar-nav">
            <button class="d-flex btn border-1 border-success ">
            <li><a class="nav-link text-dark" href="#">Trang cá nhân</a></li>
            </button>
          </ul>
        </div>
      </div>
    </nav>

    <main class="mt-6 container-sm ">
      <div class="container">
        <div class="row">
          <div class="col-md-8">
            <div class="row">
              <div class="col-md-12" v-for="baiViet in baiBiet" :key="baiViet.id">
                <div class="card mb-4 shadow">
                  <div class="d-flex">
                    <img :src="baiViet.hinhAnh" class="card-img-left" alt="Hình bài viết" />
                    <div class="card-body text-lg-start">
                      <h3 class="card-text">
                        <i class="fa-solid fa-user"></i> {{ baiViet.tacGia }} 
                        
                      </h3>
                      <h5 class="card-title">{{ baiViet.tieuDe }}</h5>
                      <p class="card-text">{{ baiViet.tomTat }}</p>
                      <p class="card-text comment-text">
                        <i class="fa-solid fa-message"></i> {{ baiViet.binhLuan }} bình luận
                      </p>
                      <a href="#" class="btn btn-primary" @click.prevent="showBlogDetail(baiViet)">Đọc thêm</a>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-md-4 fixed">
            <div v-if="showDetail" class="">
              <div class="card mb-4 shadow">
                <div class="d-flex">
                  <img :src="selectedBaiViet.avatarngdang" class="rounded-circle mr-3" alt="Avatar" />
                  <h3 class="card-text text-start me-1 my-auto ms-3"> {{ selectedBaiViet.tacGia }} </h3>
                  <p class="my-auto text-muted text-lg-start">{{ selectedBaiViet.tieuDe }}</p>
                </div>
                <p class="text-lg-start"> {{ selectedBaiViet.thoiGian }}</p>
                <div class="">
                  <img :src="selectedBaiViet.hinhAnh" class="card-img-top" alt="Hình bài viết" />
                  <div class="card-body text-lg-start">
                    <p class="card-text">{{ selectedBaiViet.tomTat }}</p>
                    <p class="card-text">{{ selectedBaiViet.noiDung }}</p>
                    <p class="card-text comment-text">
                      <i class="fa-solid fa-message"></i> {{ selectedBaiViet.binhLuan }} bình luận
                    </p>
                    <div class="mt-3">
                      <h5>Bình luận:</h5>
                      <ul class="">
                        <li v-for="(comment, index) in selectedBaiViet.comments" :key="index">
                          <strong>{{ comment.user }}:</strong> {{ comment.text }}
                        </li>
                      </ul>
                    </div>
                    <div>
                      <input type="text" v-model="newComment" placeholder="Nhập bình luận của bạn" class="form-control" />
                      <button class="btn btn-primary mt-2" @click="addComment">Gửi bình luận</button>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="card mb-4 shadow">
              <div class="card-body">
                <div class="d-flex align-items-center">
                  <img :src="nguoiDung.avatar" class="rounded-circle mr-3" alt="Avatar" />
                  <div class="ms-3">
                    <h5 class="card-title">{{ nguoiDung.ten }}</h5>
                    <p class="card-text">{{ nguoiDung.friends }} người bạn</p>
                  </div>
                </div>
                <hr>
                <p class="card-text">{{ nguoiDung.moTa }}</p>
                <p class="card-text text-start">Có {{ nguoiDung.soNguoiTheoDoi }} người theo dõi</p>
                <div class="text-start">
                  <p class="card-text">Trạng thái: {{ nguoiDung.trangthai }}</p>
                  <p class="card-text">Email: {{ nguoiDung.email }}</p>
                </div>
                <br>
                <button class="btn w-100 btn-primary shadow-sm text-light">Xem trang cá nhân</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>

    <footer class="bg-light text-center text-lg-start mt-5">
      <div class="text-center p-3">
        © 2023 Blog. All rights reserved.
        <br />
        <a href="#" class="text-dark">Privacy Policy</a> |
        <a href="#" class="text-dark">Terms of Service</a>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const nguoiDung = ref({
  avatar: 'https://via.placeholder.com/50',
  ten: 'Nguyễn Trí Tài',
  friends: 86,
  moTa: 'Mỗi ngày là 1 niềm vui',
  trangthai: '1 vợ 2 con',
  email: 'test1@gmail.com',
  soNguoiTheoDoi: 635
});

const baiBiet = ref([
  {
    id: 1,
    avatarngdang: 'https://via.placeholder.com/50',
    tieuDe: 'Bài Viết 1',
    tomTat: 'Tóm tắt bài viết 1...',
    noiDung: 'Nội dung chi tiết của bài viết 1...',
    hinhAnh: 'https://via.placeholder.com/150',
    tacGia: 'Tèo',
    thoiGian: '03/11/2024',
    binhLuan: 2,
    comments: [
      { user: 'Nguyễn Văn A', text: 'Bài viết rất hay, cảm ơn bạn!' },
      { user: 'Trần Thị B', text: 'Mình cũng có ý kiến tương tự!' }
    ]
  },
  {
    id: 2,
    avatarngdang: 'https://via.placeholder.com/50',
    tieuDe: 'Bài Viết 2',
    tomTat: 'Tóm tắt bài viết 2...',
    noiDung: 'Nội dung chi tiết của bài viết 2...',
    hinhAnh: 'https://via.placeholder.com/150',
    tacGia: 'Nở',
    thoiGian: '03/11/2024',
    binhLuan: 2,
    comments: [
      { user: 'Lê Văn C', text: 'Rất thú vị, mình đã học được nhiều điều!' },
      { user: 'Phạm Thị D', text: 'Nội dung rất bổ ích, cảm ơn!' }
    ]
  },
  {
    id: 3,
    avatarngdang: 'https://via.placeholder.com/50',
    tieuDe: 'Bài Viết 3',
    tomTat: 'Tóm tắt bài viết 3...',
    noiDung: 'Nội dung chi tiết của bài viết 3...',
    hinhAnh: 'https://via.placeholder.com/150',
    tacGia: 'Phèo',
    thoiGian: '03/11/2024',
    binhLuan: 2,
    comments: [
      { user: 'Nguyễn Thị E', text: 'Bài viết rất hay, mình thích cách hành văn của bạn!' },
      { user: 'Trần Văn F', text: 'Cảm ơn đã chia sẻ kiến thức!' }
    ]
  },
  {
    id: 4,
    avatarngdang: 'https://via.placeholder.com/50',
    tieuDe: 'Bài Viết 4',
    tomTat: 'Tóm tắt bài viết 4...',
    noiDung: 'Nội dung chi tiết của bài viết 4...',
    hinhAnh: 'https://via.placeholder.com/150',
    tacGia: 'Hùng',
    thoiGian: '04/11/2024',
    binhLuan: 2,
    comments: [
      { user: 'Lê Văn G', text: 'Thông tin rất hữu ích, cảm ơn bạn!' },
      { user: 'Nguyễn Thị H', text: 'Mong bạn viết thêm nhiều bài như vậy!' }
    ]
  },
  {
    id: 5,
    avatarngdang: 'https://via.placeholder.com/50',
    tieuDe: 'Bài Viết 5',
    tomTat: 'Tóm tắt bài viết 5...',
    noiDung: 'Nội dung chi tiết của bài viết 5...',
    hinhAnh: 'https://via.placeholder.com/150',
    tacGia: 'Linh',
    thoiGian: '05/11/2024',
    binhLuan: 2,
    comments: [
      { user: 'Phạm Văn I', text: 'Bài viết rất truyền cảm hứng!' },
      { user: 'Trần Thị J', text: 'Mình sẽ theo dõi thêm bài viết của bạn!' }
    ]
  },
  {
    id: 6,
    avatarngdang: 'https://via.placeholder.com/50',
    tieuDe: 'Bài Viết 5',
    tomTat: 'Tóm tắt bài viết 5...',
    noiDung: 'Nội dung chi tiết của bài viết 5...',
    hinhAnh: 'https://via.placeholder.com/150',
    tacGia: 'Linh',
    thoiGian: '05/11/2024',
    binhLuan: 2,
    comments: [
      { user: 'Phạm Văn I', text: 'Bài viết rất truyền cảm hứng!' },
      { user: 'Trần Thị J', text: 'Mình sẽ theo dõi thêm bài viết của bạn!' }
    ]
  }
]);

const showDetail = ref(false);
const selectedBaiViet = ref(null);
const newComment = ref('');

const showBlogDetail = (baiViet) => {
  selectedBaiViet.value = baiViet;
  showDetail.value = true;
};

const addComment = () => {
  if (newComment.value.trim() === '') return;
  selectedBaiViet.value.binhLuan += 1;
  selectedBaiViet.value.comments.push({ user: nguoiDung.value.ten, text: newComment.value });
  newComment.value = '';
};
</script>

<style>

.card {
  padding: 2em;
}
@media (prefers-color-scheme: light) {
  :root {
    color: #213547;
    background-color: #ffffff;
  }
  a:hover {
    color: #747bff;
  }
  button {
    background-color: #f9f9f9;
  }
}
html, body {
  margin: 0;
  padding: 0;
  font-family: Arial, sans-serif;
}

main {
  padding: 20px;
  margin-top: 56px; /* Height of the fixed navbar */
}

.card {
  border: 1px solid #ddd;
  border-radius: 0.5rem;
  transition: transform 0.2s;
}

.card:hover {
  transform: scale(1.02);
}

.card-img-left {
  height: 200px;
  width: 150px;
  object-fit: cover;
  border-radius: 0.5rem 0 0 0.5rem; /* Rounded corners on the left */
}

.card-body {
  flex: 1;
}

footer {
  position: relative;
  bottom: 0;
  width: 100%;
  padding: 10px 0;
  background-color: #f8f9fa;
  color: #333;
}

.btn-primary {
  background-color: #007bff;
  border: none;
}

.btn-primary:hover {
  background-color: #0056b3;
}

.comment-text {
  color: #1be600; /* Comment text color */
}
.col-md-4.fixed {
  position: sticky;
  top: 70px; /* Khoảng cách từ trên xuống (để không bị che bởi navbar cố định) */
  height: fit-content;
}

</style>
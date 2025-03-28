<template>
    <div class="row container-lg">
      <section class="row">
        <aside class="col-sm-6 bg-light">
          <h2 class="text-info mb-3">Trang blog</h2>
          <div class="card mb-3">
            <img src="../assets/images/avatar.png" class="card-img-top" alt="Hình đại diện" />
            <div class="card-body">
              <h5 class="card-title">Giới thiệu bản thân mình</h5>
              <p class="card-text">
                Trang blog nơi chia sẽ các bài viết của mình, kết nối với mọi người, bình luận các bài biết khác nhau, tô màu cho cuộc sống
              </p>
            </div>
          </div>
        </aside>
  
        <article class="col-sm-6">
          <div>
            <!-- Form đăng nhập -->
            <div class="container" id="login" v-show="isLogin">
              <h1>Chào mừng sự trở lại</h1>
              <form @submit.prevent="handleLogin" class="border p-3">
                <div class="mb-3 mt-3 text-start">
                  <label for="loginEmail" class="form-label">Email:</label>
                  <input type="email" class="form-control" id="loginEmail" placeholder="Mời nhập email" v-model="loginEmail" />
                </div>
                <div class="mb-3 text-start">
                  <label for="loginPwd" class="form-label">Password:</label>
                  <input type="password" class="form-control" id="loginPwd" placeholder="Nhập mật khẩu" v-model="loginPassword" />
                  <div class="d-flex">
                    <a href="#" @click.prevent="showRegister">Đăng kí</a>
                    <a class="ms-auto" href="#" @click.prevent="showForgotPassword">Quên mật khẩu</a>
                  </div>
                </div>
                <div class="text-start">
                  <button type="submit" class="btn btn-primary">Đăng nhập</button>
                </div>
              </form>
            </div>
            
            <!-- Form đăng kí -->
            <div class="container" id="register" v-show="!isLogin">
              <h1>Xin chào thành viên mới</h1>
              <form @submit.prevent="handleRegister" class="border p-3">
                <div class="mb-3 mt-3 text-start">
                  <label for="fullName" class="form-label">Họ và Tên:</label>
                  <input type="text" class="form-control" id="fullName" v-model="fullName" required placeholder="Nhập họ và tên" />
                </div>
                <div class="mb-3 text-start">
                  <label for="registerEmail" class="form-label">Email:</label>
                  <input type="email" class="form-control" id="registerEmail" v-model="registerEmail" required placeholder="Nhập email" />
                </div>
                <div class="mb-3 text-start">
                  <label for="phone" class="form-label">Số điện thoại:</label>
                  <input type="text" class="form-control" id="phone" v-model="phone" required placeholder="Nhập số điện thoại" />
                </div>
                <div class="mb-3 text-start">
                  <label for="registerPwd" class="form-label">Mật khẩu:</label>
                  <input type="password" class="form-control" id="registerPwd" v-model="registerPassword" required placeholder="Nhập mật khẩu" />
                </div>
                <div class="mb-3 text-start">
                  <label for="confirmPwd" class="form-label">Xác nhận mật khẩu:</label>
                  <input type="password" class="form-control" id="confirmPwd" v-model="confirmPassword" required placeholder="Xác nhận mật khẩu" />
                </div>
                <div class="mb-3 text-start">
                  Giới tính:
                  <div class="form-check form-check-inline">
                    <input type="radio" class="form-check-input" id="genderMale" v-model="gender" value="male" />
                    <label class="form-check-label" for="genderMale">Nam</label>
                  </div>
                  <div class="form-check form-check-inline">
                    <input type="radio" class="form-check-input" id="genderFemale" v-model="gender" value="female" />
                    <label class="form-check-label" for="genderFemale">Nữ</label>
                  </div>
                </div>
                <div class="mb-3 text-start">
                  <label class="form-label">Ngôn ngữ</label>
                  <select class="form-select" v-model="language">
                    <option>Tiếng Việt</option>
                    <option>Tiếng La-Tin</option>
                    <option>Tiếng Hán Việt</option>
                    <option>Tiếng nôm</option>
                  </select>
                </div>
                <div class="d-flex form-check mb-3 text-start">
                  <input class="form-check-input" type="checkbox" v-model="agreeTerms" />
                  <label class="form-check-label">Tôi đồng ý với các điều khoản và điều kiện.</label>
                  <a class="ms-auto" href="#" @click.prevent="showLogin">Đăng nhập</a>
                </div>
                <div class="text-start">
                  <button type="submit" class="btn btn-primary">Submit</button>
                </div>
              </form>
            </div>
  
            <!-- Quên mật khẩu Modal -->
            <div class="modal" tabindex="-1" v-show="isForgotPassword" @click.self="closeForgotPassword">
              <div class="modal-dialog">
                <div class="modal-content">
                  <div class="modal-header">
                    <h5 class="modal-title">Quên mật khẩu</h5>
                    <button type="button" class="btn-close border-0" @click="closeForgotPassword">x</button>
                  </div>
                  <div class="modal-body">
                    <form @submit.prevent="handleForgotPassword">
                      <div class="mb-3">
                        <label for="forgotEmail" class="form-label">Nhập email của bạn:</label>
                        <input type="email" class="form-control" id="forgotEmail" v-model="forgotEmail" required />
                      </div>
                      <button type="submit" class="btn btn-primary">Gửi yêu cầu</button>
                    </form>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </article>
      </section>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const isLogin = ref(true);
  const isForgotPassword = ref(false);
  const loginEmail = ref('');
  const loginPassword = ref('');
  const fullName = ref('');
  const registerEmail = ref('');
  const phone = ref('');
  const registerPassword = ref('');
  const confirmPassword = ref('');
  const gender = ref('male');
  const language = ref('Tiếng Việt');
  const agreeTerms = ref(false);
  const forgotEmail = ref('');
  
  function showLogin() {
    isLogin.value = true;
    isForgotPassword.value = false;
  }
  
  function showRegister() {
    isLogin.value = false;
    isForgotPassword.value = false;
  }
  
  function showForgotPassword() {
    isForgotPassword.value = true;
  }
  
  function closeForgotPassword() {
    isForgotPassword.value = false;
  }
  
  function handleLogin() {
    // Handle login logic here
    console.log('Logging in with:', loginEmail.value, loginPassword.value);
  }
  
  function handleRegister() {
    // Handle registration logic here
    console.log('Registering with:', fullName.value, registerEmail.value, phone.value, registerPassword.value);
  }
  
  function handleForgotPassword() {
    // Handle forgot password logic here
    console.log('Sending reset password email to:', forgotEmail.value);
    closeForgotPassword(); // Close modal after submitting
  }
  </script>
  
  <style>
  .modal {
    display: block; /* Show modal */
    position: fixed;
    z-index: 1050;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    background-color: rgba(0, 0, 0, 0.5); /* Background overlay */
  }
  
  .modal-dialog {
    position: relative;
    margin: 1.75rem auto; /* Center modal */
  }
  
  .modal-content {
    border: none;
    border-radius: 0.5rem;
  }
  
  .modal-header {
    border-bottom: none;
  }
  
  .modal-title {
    margin: 0;
  }
  
  .modal-body {
    padding: 1rem;
  }
  
  .btn-close {
    background: transparent;
    border: none;
  }
  </style>
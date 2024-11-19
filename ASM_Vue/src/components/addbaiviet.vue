<template>
    <div class="container mt-5">
        <h1 class="text-center">Chỉnh sửa Trang Cá Nhân</h1>
        <form id="profileForm" class="row">
            <div class="col-md-4 form-group">
                <label for="avatar">Ảnh đại diện:</label>
                <div class="avatar-container" onclick="document.getElementById('avatar').click();">
                    <img id="avatarPreview" class="avatar-preview" src="" alt="Avatar Preview">
                    <input type="file" id="avatar" accept="image/*" onchange="previewAvatar(event)" style="display: none;">
                    <span class="text-center">Nhấp để thay đổi ảnh</span>
                </div>
            </div>
            <div class="col-md-8">
                <div class="form-group">
                    <label for="username">Tên người dùng:</label>
                    <input type="text" class="form-control" id="username" required>
                </div>
                <div class="form-group">
                    <label for="title">Tiêu đề:</label>
                    <input type="text" class="form-control" id="title">
                </div>
                <div class="form-group">
                    <label for="maritalStatus">Trạng thái hôn nhân:</label>
                    <select class="form-control" id="maritalStatus">
                        <option value="">Chọn trạng thái</option>
                        <option value="Độc thân">Độc thân</option>
                        <option value="Đã kết hôn">Đã kết hôn</option>
                        <option value="Ly hôn">Ly hôn</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="location">Nơi sinh sống:</label>
                    <input type="text" class="form-control" id="location">
                </div>
                <div class="form-group">
                    <label for="job">Công việc:</label>
                    <input type="text" class="form-control" id="job">
                </div>
                <div class="form-group">
                    <label for="email">Email:</label>
                    <input type="email" class="form-control" id="email" required>
                </div>
                <div class="form-group">
                    <label for="password">Mật khẩu:</label>
                    <input type="password" class="form-control" id="password" required>
                </div>
                <div class="form-group">
                    <label for="bio">Giới thiệu:</label>
                    <textarea class="form-control" id="bio" rows="4"></textarea>
                </div>
                <button type="submit" class="btn btn-success btn-block">Lưu Thay Đổi</button>
            </div>
        </form>

        <h2 class="col-md-8 mt-5 text-center">Đăng Bài Viết Mới</h2>
        <form id="postForm">
            <div class="form-group">
                <label for="postTitle">Tiêu đề:</label>
                <input type="text" class="form-control" id="postTitle" required>
            </div>
            <div class="form-group">
                <label for="postContent">Nội dung:</label>
                <textarea class="form-control" id="postContent" rows="6" required></textarea>
            </div>
            <button type="submit" class="btn btn-primary btn-block">Đăng Bài</button>
        </form>
    </div>
</template>

<script>
    function previewAvatar(event) {
        const file = event.target.files[0];
        const preview = document.getElementById('avatarPreview');
        if (file) {
            const reader = new FileReader();
            reader.onload = function(e) {
                preview.src = e.target.result;
                preview.style.display = 'block';
            }
            reader.readAsDataURL(file);
        } else {
            preview.src = '';
            preview.style.display = 'none';
        }
    }
</script>

<style>
    .avatar-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        cursor: pointer;
        border: 2px dashed #007bff;
        border-radius: 50%;
        width: 150px;
        height: 150px;
        justify-content: center;
        margin: 10px auto;
        position: relative;
    }
    .avatar-preview {
        border-radius: 50%;
        width: 100%;
        height: 100%;
        object-fit: cover;
        display: none;
    }
</style>
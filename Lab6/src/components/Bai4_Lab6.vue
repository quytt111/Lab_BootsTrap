<template>
  <div class="row container">
    <form @submit.prevent="themSinhVien" action="" class="col-sm-4">
      <h1>Thêm học sinh</h1>
      <label class="text-muted" for="">Họ tên:</label>
      <br>
      <input class="form-control" v-model="sinhVienN.name" type="text" />
      <br />
      <br>
      <label class="text-muted" for="">Điểm</label>
      <br>
      <input class="form-control" v-model="sinhVienN.diem" type="number"/>
      <br />
      <br>
      <label class="text-muted" for="">Ngày sinh</label>
      <br>
      <input class="form-control" v-model="sinhVienN.ngaySinh" type="date" />
      <br />
      <button type="submit" class="btn btn-success">Thêm</button>
      <p v-if="errorMessage" class="text-danger">{{ errorMessage }}</p>
    </form>
    <div class="col-sm-8">
      <h1>Danh sách học sinh</h1>
      <table class="table table-hover">
        <thead>
          <tr>
            <th>Họ và tên</th>
            <th>Điểm</th>
            <th>Ngày sinh</th>
            <th>Học lực</th>
            <th></th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="sinhVien in danhSach" :key="sinhVien.id">
            <td>{{ sinhVien.name }}</td>
            <td>{{ sinhVien.diem }}</td>
            <td>{{ sinhVien.ngaySinh }}</td>
            <td>
              <p v-if="Number(sinhVien.diem) >= 11">10đ là tối đa xin nhập lại</p>
              <p v-else-if="Number(sinhVien.diem) >= 9">Xuất sắc</p>
              <p v-else-if="Number(sinhVien.diem) >= 8">Giỏi</p>
              <p v-else-if="Number(sinhVien.diem) >= 6.5">Khá</p>
              <p v-else-if="Number(sinhVien.diem) >= 5">Trung bình</p>
              <p v-else>Yếu</p>
             
            </td>
            <td>
              <button class="btn btn-warning" @click="suaSinhVien(sinhVien)">
                sửa
              </button>
            </td>
            <td>
              <button class="btn btn-danger" @click="xoaSinhvien(sinhVien.id)">
                Xóa
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
const danhSach = ref([
  {
    id: 1,
    name: "Nguyễn Chí Hùng",
    diem: "8",
    ngaySinh: "2006-01-01",
  },
  {
    id: 2,
    name: "Nguyễn Thị Lan",
    diem: "9",
    ngaySinh: "2006-05-15",
  },
]);
const sinhVienN = ref({
  name: "",
  diem: "",
  ngaySinh: "",
});
const xoaSinhvien = (id) => {
  danhSach.value = danhSach.value.filter((sinhVien) => sinhVien.id != id);
};
const errorMessage = ref("");
const isSua = ref(false);
const suaTheoId = ref(null);
const themSinhVien = () => {
  if (
    !sinhVienN.value.name ||
    !sinhVienN.value.diem || 
    sinhVienN.value.diem >=11 ||
    !sinhVienN.value.ngaySinh
  ) {
    errorMessage.value =
      "Vui lòng điền đầy đủ thông tin (Họ tên, Điểm (Lớn nhất là 10 và nhỏ nhất là 0), Ngày sinh)";
    return;
  }
  if (isSua.value) {
    const index = danhSach.value.findIndex((sv) => sv.id === suaTheoId.value);
    if (index !== -1) {
      danhSach.value[index] = {
        id: suaTheoId.value,
        name: sinhVienN.value.name,
        diem: sinhVienN.value.diem,
        ngaySinh: sinhVienN.value.ngaySinh,
      };
    }
  } else {
    danhSach.value.push({
      id: Date.now(),
      name: sinhVienN.value.name,
      diem: sinhVienN.value.diem,
      ngaySinh: sinhVienN.value.ngaySinh,
    });
  }
  sinhVienN.value = { name: "", diem: "", ngaySinh: "" };
  errorMessage.value = "";
  isSua = false;
  suaTheoId.value = null;
};
const suaSinhVien = (sinhVien) => {
  sinhVienN.value = { ...sinhVien };
  isSua.value = true;
  suaTheoId.value = sinhVien.id;
  errorMessage.value = "";
};
</script>

<style></style>

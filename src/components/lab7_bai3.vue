<template>
    <div class="p-5 col-sm-6">
      <h3 class="text-center">Form Đăng ký người dùng</h3>
      <!-- Form đăng ký -->
      <form @submit.prevent="register">
        <div class="mb-3">
          <label>Họ tên:</label>
          <input
            type="text"
            class="form-control"
            v-model="fullName"
            placeholder="Nhập họ tên"
          />
          <p v-if="fullNameError" style="color: red;">{{ fullNameError }}</p>
        </div>
        <div class="mb-3">
          <label>Email:</label>
          <input
            type="email"
            class="form-control"
            v-model="email"
            placeholder="Nhập email"
          />
          <p v-if="emailError" style="color: red;">{{ emailError }}</p>
        </div>
        <div class="mb-3">
          <label>Mật khẩu:</label>
          <input
            type="password"
            class="form-control"
            v-model="password"
            placeholder="Nhập mật khẩu"
          />
          <p v-if="passwordError" style="color: red;">{{ passwordError }}</p>
        </div>
        <div class="mb-3">
          <label>Ngày sinh:</label>
          <input
            type="date"
            class="form-control"
            v-model="birthDate"
          />
        </div>
        <div class="mb-3">
          <label>Giới tính:</label>
          <select class="form-control" v-model="gender">
            <option value="">Chọn giới tính</option>
            <option value="Nam">Nam</option>
            <option value="Nữ">Nữ</option>
            <option value="Khác">Khác</option>
          </select>
        </div>
        <div class="mb-3">
          <label>Ngôn ngữ:</label>
          <select class="form-control" v-model="language">
            <option value="">Chọn ngôn ngữ</option>
            <option value="Tiếng Việt">Tiếng Việt</option>
            <option value="Tiếng Anh">Tiếng Anh</option>
            <option value="Tiếng Nhật">Tiếng Nhật</option>
          </select>
        </div>
        <button type="submit" class="btn btn-primary">Đăng ký</button>
      </form>
  
      <!-- Hiển thị thông tin đã đăng ký -->
      <div v-if="isRegistered" class="mt-5">
        <h3 class="text-center">Thông tin đăng ký</h3>
        <p><strong>Họ tên:</strong> {{ fullName }}</p>
        <p><strong>Email:</strong> {{ email }}</p>
        <p><strong>Ngày sinh:</strong> {{ birthDate }}</p>
        <p><strong>Giới tính:</strong> {{ gender }}</p>
        <p><strong>Ngôn ngữ:</strong> {{ language }}</p>
      </div>
    </div>
  </template>
<script setup>
import { ref } from 'vue';

const fullName = ref('');
const email = ref('');
const password = ref('');
const birthDate = ref('');
const gender = ref('');
const language = ref('');
const isRegistered = ref(false);

const fullNameError = ref('');
const emailError = ref('');
const passwordError = ref('');

const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

const register = () => {
  // Reset thông báo lỗi
  fullNameError.value = '';
  emailError.value = '';
  passwordError.value = '';

  let isValid = true;

  // Validate họ tên
  if (!fullName.value.trim()) {
    fullNameError.value = 'Họ tên là bắt buộc.';
    isValid = false;
  }

  // Validate email
  if (!email.value.trim()) {
    emailError.value = 'Email là bắt buộc.';
    isValid = false;
  } else if (!emailRegex.test(email.value)) {
    emailError.value = 'Vui lòng nhập email hợp lệ.';
    isValid = false;
  }

  // Validate mật khẩu
  if (!password.value.trim()) {
    passwordError.value = 'Mật khẩu là bắt buộc.';
    isValid = false;
  }

  // Nếu không có lỗi, đăng ký thành công
  if (isValid) {
    isRegistered.value = true;
  }
};
</script>
  
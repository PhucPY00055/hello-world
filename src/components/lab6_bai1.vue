<template>
    <div class="container">
      <h3>Nhập điểm trung bình của học sinh:</h3>
      <input type="number" v-model.number="diemTB" placeholder="Nhập điểm từ 0 đến 10" class="form-control" />
      <p v-if="diemTB < 0 || diemTB > 10" style="color: red">Vui lòng nhập điểm từ 0 đến 10!</p>
      <p v-else-if="diemTB < 5.0">Xếp loại: Yếu</p>
      <p v-else-if="diemTB < 6.5">Xếp loại: Trung Bình</p>
      <p v-else-if="diemTB < 8.0">Xếp loại: Khá</p>
      <p v-else-if="diemTB < 9.0">Xếp loại: Giỏi</p>
      <p v-else>Xếp loại: Xuất Sắc</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const diemTB = ref(0);
  </script>
  
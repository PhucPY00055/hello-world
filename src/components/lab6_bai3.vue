<template>
    <div class="container mt-5">
      <h1 class="text-center mb-4">Kiến thức sức khỏe cộng đồng</h1>
      <div class="row">
        <div class="col-sm-4" v-for="(item, index) in items" :key="index">
          <div class="card h-100 d-flex flex-column">
            <img :src="item.image" class="card-img-top img-fluid" alt="Hình ảnh" />
            <div class="card-body flex-grow-1 d-flex flex-column">
              <h3 class="card-title">{{ item.title }}</h3>
              <p class="card-text flex-grow-1">{{ item.content }}</p>
              <button class="btn btn-info mt-auto">Xem chi tiết</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import img1 from '../components/images/fruit.jpg';
  import img2 from '../components/images/giavi.jpg';
  import img3 from '../components/images/dau.jpg';
  
  // Danh sách các mục hiển thị
  const items = [
    {
      title: '8 loại rau củ quả giàu canxi',
      content:
        'Canxi là khoáng chất cần thiết đối với cơ thể người. Có nhiều cách để bổ sung canxi, trong đó bổ sung qua đường ăn uống là cách tốt nhất. Có 8 loại rau củ giàu canxi...',
      image: img1,
    },
    {
      title: 'Các loại gia vị tốt cho sức khỏe',
      content:
        'Một số loại gia vị cung cấp nhiều polyphenol chống oxy hóa cao hơn các loại gia vị quen thuộc khác. Với một lượng nhỏ, các món ăn đã thêm hương thơm và vị hấp dẫn...',
      image: img2,
    },
    {
      title: '9 loại đậu bổ dưỡng nên dùng nhiều',
      content:
        'Đậu lăng, đậu nành, đậu phộng, đậu Hà Lan giàu chất xơ, protein cùng nhiều vitamin và khoáng chất giúp giảm lượng đường trong máu, tốt cho tim...',
      image: img3,
    },
  ];
  </script>
  
  <style scoped>
  .card-img-top {
    object-fit: cover; /* Giữ ảnh vừa khung mà không bị méo */
    height: 200px; /* Chiều cao đồng nhất cho các ảnh */
  }
  .card-title {
    font-size: 1.25rem; /* Cân chỉnh tiêu đề */
  }
  </style>
  
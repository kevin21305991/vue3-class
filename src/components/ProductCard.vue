<script setup></script>

<template>
  <!-- Card -->
  <div class="card">
    <div class="card-top">
      <img
        src="https://res.cloudinary.com/djvyud0lx/image/upload/v1724144090/product01_t9wo2n.jpg"
        alt=""
      />
    </div>
    <div class="card-bottom">
      <h3 class="title">吉伊</h3>
      <p>chiikawa 娃娃</p>
      <div class="price">$500</div>
      <div class="add-cart">加入購物車</div>
    </div>
  </div>
  <div class="card">
    <div class="card-top">
      <img
        src="https://res.cloudinary.com/djvyud0lx/image/upload/v1724144090/product02_wgo6z8.jpg"
        alt=""
      />
    </div>
    <div class="card-bottom">
      <h3 class="title">小八</h3>
      <p>chiikawa 娃娃</p>
      <div class="price">$500</div>
      <div class="add-cart">加入購物車</div>
    </div>
  </div>
  <div class="card">
    <div class="card-top">
      <img
        src="https://res.cloudinary.com/djvyud0lx/image/upload/v1724144090/product03_vjujwe.jpg"
        alt=""
      />
    </div>
    <div class="card-bottom">
      <h3 class="title">烏薩奇</h3>
      <p>chiikawa 娃娃</p>
      <div class="price">$500</div>
      <div class="add-cart">加入購物車</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  width: calc((100% - 40px) / 3);
  background-color: #fbedca;
  border-radius: 10px;
  padding: 5px;
  .card-top {
    width: 100%;
    aspect-ratio: 1/1;
    border-radius: 5px;
    overflow: hidden;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
  .card-bottom {
    display: flex;
    flex-direction: column;
    color: #404040;
    padding: 10px 5px 5px;
    border-radius: 10px;
    p {
      margin-top: 10px;
    }
    .price {
      color: #78a5bc;
      font-size: 20px;
      margin-top: 10px;
    }
    .add-cart {
      color: #404040;
      background-color: #fcbfc7;
      border-radius: 5px;
      padding: 8px 6px;
      margin: 10px 0 0 auto;
      cursor: pointer;
    }
  }
}
</style>

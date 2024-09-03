<script setup>
const props = defineProps({
  data: {
    type: Object,
    required: true
  },
  addCart: {
    type: Function,
    default: () => {}
  }
});
</script>

<template>
  <!-- Card -->
  <div class="card">
    <div class="card-top">
      <img :src="props.data.imgUrl" alt="" />
    </div>
    <div class="card-bottom">
      <h3 class="title">{{ props.data.title }}</h3>
      <p>{{ props.data.description }}</p>
      <div class="price">${{ props.data.price }}</div>
      <div class="add-cart" @click="props.addCart">加入購物車</div>
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

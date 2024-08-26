<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import Navbar from '@/components/Navbar.vue';
import Footer from '@/components/Footer.vue';
import Slider from '@/components/Slider.vue';
import ProductCard from '@/components/ProductCard.vue';

const apiBaseUrl = 'https://vue3-tutorial-api.vercel.app/api';
const banners = ref([]);
const products = ref([]);
const alerts = ref([]);

// 加入購物車
const addCart = (product) => {
  console.log(`您已將 ${product.title} 商品加入購物車`);
  alerts.value.push({
    message: `您已將 ${product.title} 商品加入購物車`
  });
  setTimeout(() => {
    alerts.value.shift();
  }, 3000);
};

const getBanner = async () => {
  const response = await axios.get(`${apiBaseUrl}/banner`);
  banners.value = response.data;
};

const getProducts = async () => {
  const response = await axios.get(`${apiBaseUrl}/products`);
  products.value = response.data;
};

onMounted(() => {
  getBanner();
  getProducts();
});
</script>

<template>
  <div class="alert-contain">
    <TransitionGroup name="alert" tag="div">
      <template v-for="item in alerts" :key="item">
        <div class="message-item">{{ item.message }}</div>
      </template>
    </TransitionGroup>
  </div>
  <Navbar />
  <main>
    <section class="banner">
      <Slider :images="banners" />
    </section>
    <section class="product">
      <h2>Products</h2>
      <div class="container">
        <div class="product-list">
          <ProductCard v-for="item in products" :key="item.id" :data="item" :add-cart="addCart" />
        </div>
      </div>
    </section>
  </main>
  <Footer />
</template>

<style lang="scss" scoped>
.alert-contain {
  position: fixed;
  top: 100px;
  right: 20px;
  z-index: 10;
  > div {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }
  .message-item {
    font-size: 18px;
    padding: 12px 15px;
    border-radius: 10px;
    background-color: #f8bdc5;
    &:not(:first-child) {
      margin-top: 10px;
    }
  }
}
.alert-enter-active,
.alert-leave-active {
  transition:
    opacity 0.5s,
    transform 0.5s;
}
.alert-enter-from,
.alert-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
.banner {
  padding: 10px 0;
}
.product {
  padding: 30px 0;
  h2 {
    color: #404040;
    font-size: 30px;
    text-align: center;
    margin-bottom: 30px;
  }
  .container {
    width: min(85%, 800px);
    margin: 0 auto;
  }
  .product-list {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }
}
</style>

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
// 用來存通知的陣列
const alerts = ref([]);

// 獲取Banner資料
const getBanner = async () => {
  const response = await axios.get(`${apiBaseUrl}/banner`);
  banners.value = response.data;
};

// 獲取產品資料
const getProducts = async () => {
  const response = await axios.get(`${apiBaseUrl}/products`);
  products.value = response.data;
};

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

onMounted(() => {
  getBanner();
  getProducts();
});
</script>

<template>
  <Navbar />
  <main>
    <div class="alert-contain">
      <div>
        <div v-for="item in alerts" :key="item" class="message-item">{{ item.message }}</div>
      </div>
    </div>
    <section class="banner">
      <Slider :images="banners" />
    </section>
    <section class="product">
      <h2>Products</h2>
      <div class="container">
        <div class="product-list">
          <ProductCard
            v-for="item in products"
            :key="item.id"
            :data="item"
            :add-cart="
              () => {
                addCart(item);
              }
            "
          />
        </div>
      </div>
    </section>
  </main>
  <Footer />
</template>

<style scoped>
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

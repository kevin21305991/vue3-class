<script setup>
import Navbar from '@/components/Navbar.vue';
import Footer from '@/components/Footer.vue';
import Slider from '@/components/Slider.vue';
import ProductCard from '@/components/ProductCard.vue';
</script>

<template>
  <Navbar />
  <main>
    <section class="banner">
      <Slider />
    </section>
    <section class="product">
      <h2>Products</h2>
      <div class="container">
        <div class="product-list">
          <ProductCard />
        </div>
      </div>
    </section>
  </main>
  <Footer />
</template>

<style scoped>
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

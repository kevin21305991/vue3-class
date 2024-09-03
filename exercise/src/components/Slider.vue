<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
const props = defineProps({
  images: {
    type: Array,
    required: true
  }
});

let timer = null;
const activeIndex = ref(0);

const prev = () => {
  activeIndex.value--;
  if (activeIndex.value < 0) {
    activeIndex.value = props.images.length - 1;
  }
};

const next = () => {
  activeIndex.value++;
  if (activeIndex.value > props.images.length - 1) {
    activeIndex.value = 0;
  }
};

onMounted(() => {
  timer = setInterval(() => {
    next();
  }, 5000);
});

onUnmounted(() => {
  clearInterval(timer);
});
</script>

<template>
  <div class="slider-wrapper">
    <div class="img-box">
      <img
        v-for="(item, index) in props.images"
        v-show="activeIndex === index"
        :key="item.id"
        :src="item.imgUrl"
        alt=""
      />
    </div>
    <div class="slider-nav prev" @click="prev"></div>
    <div class="slider-nav next" @click="next"></div>
  </div>
</template>

<style lang="scss" scoped>
.slider-wrapper {
  position: relative;
  .slider-nav {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    display: flex;
    align-items: center;
    justify-content: center;
    width: 30px;
    height: 60px;
    background-color: rgba(#fff, 0.9);
    cursor: pointer;
    &.prev {
      left: 10px;
      border-radius: 16px 4px 4px 16px;
      box-shadow: 2px 2px 4px 1px rgba(0, 0, 0, 0.5);
      &::before {
        content: '＜';
        color: #000;
        font-weight: bold;
      }
    }
    &.next {
      right: 10px;
      border-radius: 4px 16px 16px 4px;
      box-shadow: 2px 2px 4px 1px rgba(0, 0, 0, 0.5);
      &::before {
        content: '＞';
        color: #000;
        font-weight: bold;
      }
    }
  }
  .img-box {
    width: 100%;
    aspect-ratio: 1920/600;
    background-color: #eee;
    border-radius: 16px;
    overflow: hidden;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      user-select: none;
    }
  }
}
</style>

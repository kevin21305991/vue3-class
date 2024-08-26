<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
const props = defineProps({
  images: {
    type: Array,
    required: true
  }
});

let autoplayInterval;
const activeIndex = ref(0);
const prevHandler = () => {
  activeIndex.value--;
  if (activeIndex.value < 0) {
    activeIndex.value = props.images.length - 1;
  }
};
const nextHandler = () => {
  activeIndex.value++;
  if (activeIndex.value > props.images.length - 1) {
    activeIndex.value = 0;
  }
};

onMounted(() => {
  autoplayInterval = setInterval(() => {
    nextHandler();
  }, 5000);
});

onUnmounted(() => {
  clearInterval(autoplayInterval);
});
</script>

<template>
  <div class="slider-wrapper">
    <div class="img-box">
      <TransitionGroup name="fade" tag="div">
        <template v-for="(item, index) in props.images" :key="item.id">
          <img v-if="index === activeIndex" :src="item.imgUrl" alt="" />
        </template>
      </TransitionGroup>
    </div>
    <div class="slider-nav prev" @click="prevHandler"></div>
    <div class="slider-nav next" @click="nextHandler"></div>
  </div>
</template>

<style lang="scss" scoped>
.slider-wrapper {
  position: relative;
  border-radius: 16px;
  box-shadow: 2px 2px 8px rgba(#000, 0.2);
  overflow: hidden;
  .slider-nav {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    display: flex;
    align-items: center;
    justify-content: center;
    width: 30px;
    height: 60px;
    color: #000;
    font-weight: bold;
    background-color: rgba(#fff, 0.8);
    transition:
      color 0.3s,
      background-color 0.3s;
    cursor: pointer;
    &.prev {
      left: 10px;
      border-radius: 16px 4px 4px 16px;
      box-shadow: 2px 2px 8px 1px rgba(#000, 0.2);
      &::before {
        content: '＜';
      }
    }
    &.next {
      right: 10px;
      border-radius: 4px 16px 16px 4px;
      box-shadow: 2px 2px 8px 1px rgba(#000, 0.2);
      &::before {
        content: '＞';
      }
    }
    &:hover {
      color: #fff;
      background-color: #79a6bd;
    }
  }
  .img-box {
    position: relative;
    width: 100%;
    height: 0;
    padding-bottom: 31.25%; //1920x600
    background-color: #eee;
    img {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      user-select: none;
    }
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>

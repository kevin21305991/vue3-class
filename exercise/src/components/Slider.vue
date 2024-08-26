<script setup></script>

<template>
  <div class="slider-wrapper">
    <div class="img-box">
      <img
        src="https://res.cloudinary.com/djvyud0lx/image/upload/v1724145009/banner01_fky9h7.jpg"
        alt=""
      />
    </div>
    <div class="slider-nav prev"></div>
    <div class="slider-nav next"></div>
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
        content: '>';
        color: #000;
        font-weight: bold;
      }
    }
  }
  .img-box {
    width: 100%;
    aspect-ratio: 2550/1500;
    background-color: #eee;
    border-radius: 16px;
    overflow: hidden;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
}
</style>

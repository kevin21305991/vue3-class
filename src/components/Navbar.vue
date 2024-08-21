<script setup></script>

<template>
  <!-- Nav -->
  <nav>
    <a href="javascript:;">
      <h1>Vue3 幼幼班</h1>
    </a>
    <ul>
      <li><a href="javascript:;">About</a></li>
      <li><a href="javascript:;">News</a></li>
      <li><a href="javascript:;">Product</a></li>
      <li><a href="javascript:;">Contact</a></li>
    </ul>
    <!--       <div class="menu-btn">
        <span></span>
        <span></span>
        <span></span>
      </div> -->
  </nav>
</template>

<style lang="scss" scoped>
nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-radius: 16px;
  background-color: #79a6bd;
  padding: 15px 30px;
  ul {
    display: flex;
    align-items: center;
    gap: 20px;
    > li {
      font-size: 20px;
    }
  }
  .menu-btn {
    display: flex;
    flex-direction: column;
    width: 30px;
    height: 16px;
    gap: 5px;
    span {
      width: 100%;
      height: 2px;
      background-color: #fff;
    }
  }
}
</style>

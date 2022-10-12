<template>
  <div class="main-banner">
    <div class="banner-design"></div>
    <div class="banner-text">
      <h1>Pizza Maker</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "Banner",
};
</script>

<style scoped>
.main-banner {
  background-image: url("/public/img/pizza.jpg");
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  height: 500px;
  display: flex;
  overflow: hidden;
  position: relative;
}

.banner-design {
  border-radius: 20px;
  height: 500px;
  width: 500px;
  position: relative;
  left: -200px;
  margin: 0;
  background-color: rgba(233, 204, 99, 0.578);
  rotate: 50deg;
}

.banner-text {
  position: absolute;
  width: 300px;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.banner-text h1 {
  color: #fff;
  text-align: center;
  font-size: 60px;
  margin: 0;
}
</style>

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
@import url("https://fonts.googleapis.com/css2?family=Fjalla+One&display=swap");
.main-banner {
  background-image: url("../assets/banner.jpg");
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  height: 600px;
  display: flex;
  overflow: hidden;
  position: relative;
}

.banner-design {
  border-radius: 20px;
  height: 600px;
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
  font-family: "Fjalla One", sans-serif;
  font-size: 60px;
  margin: 0;
}
</style>

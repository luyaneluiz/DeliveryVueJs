<template>
  <div class="main-banner">
    <div class="banner-text">
      <h1>Pizza Maker</h1>
      <p>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Error eligendi
        facilis voluptatum aliquam veritatis repellat aut earum. Mollitia porro
        iste illo magnam consequatur modi asperiores, harum libero molestiae
        veniam nesciunt.
      </p>
    </div>
    <div class="scroll__arrow">
      <span>FAÇA SEU PEDIDO</span>
      <i class="bx bx-chevrons-down bx-lg bx-fade-down"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Banner",
};
</script>

<style scoped>
@import "boxicons";
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Fjalla+One&display=swap");
.main-banner {
  background-image: url("../assets/banner.jpg");
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  height: 95vh;
}

.banner-text {
  color: #fff;
  height: 100%;
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-left: 60px;
  background: linear-gradient(90deg, #100d0dd4, transparent);
}
.banner-text h1 {
  font-family: "Fjalla One", sans-serif;
  font-size: 60px;
  margin: 0 0 15px 0;
  width: 300px;
}

.banner-text p {
  text-align: center;
  width: 300px;
}

.scroll__arrow {
  position: absolute;
  top: 83%;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  color: #e7e7e7;
}

.scroll__arrow span {
  font-family: "Poppins", sans-serif;
  font-weight: bolder;
}

@keyframes arrowDown {
  0% {
  }
}
</style>

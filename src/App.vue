<template>
  <div>
    <Navbar :logo="logo_src" :alt="app_name" />
    <router-view />
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";

export default {
  components: {
    Navbar,
  },
  data() {
    return {
      logo_src: "/img/logo.png",
      app_name: "Make your pizza",
    };
  },
};
</script>

<style>
@import "boxicons";

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}

.main-container {
  margin: 109px 50px 0 50px;
  min-height: 250px;
}

h1 {
  text-align: center;
  font-size: 42px;
}
</style>

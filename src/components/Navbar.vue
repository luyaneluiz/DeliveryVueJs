<template>
  <div id="nav">
    <router-link to="/">
      <img :src="logo" :alt="alt" id="logo" />
    </router-link>
    <div>
      <router-link to="/">Home</router-link>
      <router-link to="/pedidos">Pedidos</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  props: ["logo", "alt"],
};
</script>

<style scoped>
#nav {
  background-color: rgb(255, 255, 255);
  border-bottom: 4px solid #7c600f;
  padding: 15px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#logo {
  width: 40px;
  height: 40px;
}

#nav a {
  color: #7c600f;
  text-decoration: none;
  margin: 12px;
  transition: 0.5s;
}

#nav a:hover {
  color: #c89708;
}
</style>

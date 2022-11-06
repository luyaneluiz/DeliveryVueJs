<template>
  <div class="main-container pedidos">
    <h1>Gerenciar Pedidos</h1>
    <Dashboard />
  </div>
</template>

<script>
import Dashboard from "../components/Dashboard.vue";

export default {
  name: "Pedidos",
  components: {
    Dashboard,
  },
};
</script>

<style>
.main-container.pedidos {
  margin: 0 50px;
  padding-top: 109px;
  height: calc(100vh - 100px);
}
</style>

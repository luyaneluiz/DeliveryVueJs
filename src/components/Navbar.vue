<template>
  <div id="nav">
    <router-link to="/">
      <img :src="logo" :alt="alt" id="logo" />
    </router-link>
    <div>
      <router-link to="/">
        <svg xmlns="http://www.w3.org/2000/svg" height="48" width="48">
          <path
            fill="#fff"
            d="M11.55 38.45h8.05v-12h8.8v12h8.05v-18.7L24 10.35l-12.45 9.4ZM10 40V19L24 8.4 38 19v21H26.85V28h-5.7v12Zm14-15.6Z"
          />
        </svg>
      </router-link>
      <router-link to="/pedidos">
        <svg xmlns="http://www.w3.org/2000/svg" height="48" width="48">
          <path
            fill="#fff"
            d="M11.6 42q-1.55 0-2.6-1.075T7.95 38.35v-4.1h6.15V6.75l2.5 1.8 2.65-1.8 2.6 1.8 2.6-1.8 2.6 1.8 2.65-1.8 2.6 1.8 2.6-1.8 2.65 1.8 2.5-1.8v31.6q0 1.5-1.05 2.575Q37.95 42 36.4 42Zm24.8-1.55q.9 0 1.525-.6.625-.6.625-1.5V9.55H15.6v24.7h18.7v4.1q0 .9.6 1.5t1.5.6ZM18.7 16.5v-1.55h10.7v1.55Zm0 6.35V21.3h10.7v1.55ZM34 17q-.5 0-.9-.375t-.4-.925q0-.5.4-.9t.9-.4q.5 0 .9.4t.4.9q0 .55-.4.925T34 17Zm0 6.25q-.5 0-.9-.4t-.4-.9q0-.55.4-.95.4-.4.9-.4t.9.4q.4.4.4.95 0 .5-.4.9t-.9.4Zm-22.45 17.2h21.2v-4.7H9.45v2.6q0 .9.625 1.5t1.475.6Zm-2.1 0v-4.7 4.7Z"
          />
        </svg>
      </router-link>
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
  position: absolute;
  z-index: 2;
  width: 100%;
  padding: 15px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: linear-gradient(180deg, #222121, transparent);
}

#logo {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}

#nav img {
  color: #7c600f;
  text-decoration: none;
  margin: 12px;
  transition: 0.5s;
}

#nav a:hover {
  color: #c89708;
}
</style>

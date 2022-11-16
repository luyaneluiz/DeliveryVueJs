<template>
  <div id="nav">
    <router-link to="/">
      <img :src="logo" :alt="alt" id="logo" />
    </router-link>
    <div class="navigator">
      <router-link to="/">
        <svg xmlns="http://www.w3.org/2000/svg" height="40" width="40">
          <path
            fill="#fff"
            d="M9.583 32.083h6.209V21.958h8.416v10.125h6.209V16.458L20 8.625 9.583 16.458ZM7.5 34.167v-18.75L20 6l12.5 9.417v18.75H22.125V24.042h-4.25v10.125ZM20 20.333Z"
          />
        </svg>
      </router-link>
      <router-link to="/pedidos">
        <svg xmlns="http://www.w3.org/2000/svg" height="40" width="40">
          <path
            fill="#fff"
            d="M9.625 35.833q-1.583 0-2.708-1.125-1.125-1.125-1.125-2.75v-4.25h5.125V4.5l2.291 1.958L15.542 4.5l2.333 1.958L20.208 4.5l2.334 1.958L24.917 4.5l2.333 1.958L29.583 4.5l2.334 1.958L34.208 4.5v27.458q0 1.625-1.125 2.75t-2.708 1.125Zm20.75-2.083q.75 0 1.25-.5t.5-1.292V7.917H13v19.791h15.583v4.25q0 .792.5 1.292t1.292.5ZM15.25 14.125v-2.083h9.458v2.083Zm0 5.292v-2.084h9.458v2.084Zm13.208-5.042q-.541 0-.916-.396t-.375-.896q0-.5.375-.875t.916-.375q.5 0 .875.375t.375.875q0 .5-.375.896t-.875.396Zm0 5.167q-.541 0-.916-.375t-.375-.875q0-.542.375-.917t.916-.375q.5 0 .875.375t.375.917q0 .5-.375.875t-.875.375ZM9.625 33.75H26.5v-3.958H7.875v2.166q0 .792.5 1.292t1.25.5Zm-1.75 0v-3.958 3.958Z"
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
  position: fixed;
  z-index: 2;
  width: 100%;
  padding: 15px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: linear-gradient(180deg, #222121, transparent);
}

#logo {
  width: 150px;
  height: 75px;
  border-radius: 50%;
}

.navigator {
  display: flex;
  gap: 15px;
}

.navigator svg:hover path {
  transition: 0.8s;
  fill: #dac3a6;
}
</style>

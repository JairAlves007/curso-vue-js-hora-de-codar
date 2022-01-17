<template>
  <div id="nav">
    <router-link to="/">
      <img :src="logo" :alt="alt" id="logo">
    </router-link>

    <div class="menu">
      <router-link to="/">Home</router-link> |
      <router-link to="/pedidos">Pedidos</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  props: {
    logo: String,
    alt: String
  }
};
</script>

<style scoped>
#nav {
  background-color: #222;
  border-bottom: 4px solid #111;
  padding: 15px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#nav img {
  width: 60px;
  height: 60px;
}

#nav a {
  color: #FCBA03;
  text-decoration: none;
  margin: 12px;
  transition: .5s;
}

#nav a:hover {
  color: #fff;
}
</style>
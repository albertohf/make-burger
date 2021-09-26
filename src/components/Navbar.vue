<template>
  <div id="nav">
    <router-link to="/">
      <img src="../assets/burger.png" alt="Make Your Burger" id="logo" />
    </router-link>
    <div>
      <router-link to="/">Home</router-link>
      <router-link to="/requests">Requests</router-link>
    </div>
  </div>
</template>
<script>
export default {
  name: "Navbar",
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
#logo {
  width: 50px;
  height: 50px;
}
#nav a {
  color: #fcba03;
  text-decoration: none;
  margin: 12px;
  transition: 0.5s;
}
#nav a:hover {
  color: #fff;
}
</style>
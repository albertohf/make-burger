<template>
  <div id="main-banner">
    <h1>Make Your Burger</h1>
  </div>
</template>
<script>
export default {
  name: "Banner",
};
</script>
<style scoped>
#main-banner {
  background-image: url(https://raw.githubusercontent.com/matheusbattisti/curso_vue_yt/main/18_projeto/public/img/burger.jpg);
  background-position: 0 -14.375rem;
  background-repeat: no-repeat;
  background-size: cover;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  height: 31.25rem;
}
h1 {
  font-size: 3.25rem;
  background-color: rgba(95, 90, 90, 0.205);
  padding: 1.25rem 2.5rem;
  color: #fcab03;
  text-shadow: -2px 0 black, 0 2px black, 2px 0 black, 0 -2px black;
}
</style>
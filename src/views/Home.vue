<template>
  <Banner />
  <div class="mainContainer">
    <h1>Monte o seu Burger:</h1>
    <BurgerForm />
  </div>
</template>

<script>
import Banner from "../components/Banner";
import BurgerForm from "../components/BurgerForm";
export default {
  name: "Home",
  components: {
    Banner,
    BurgerForm,
  },
};
</script>
<style scoped>
</style>

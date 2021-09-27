<template>
  <Navbar />
  <router-view />
  <Footer />
</template>
<script>
import Navbar from "./components/Navbar";
import Footer from "./components/Footer";

export default {
  components: {
    Navbar,
    Footer,
  },
  data() {
    return {};
  },
};
</script>

<style>
* {
  font-family: "Helvetica";
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.mainContainer {
  margin: 3.125rem;
  min-width: 15.625rem;
}
h1 {
  text-align: center;
  font-size: 2.625rem;
  margin-bottom: 1.875rem;
  color: #222;
}
</style>

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
  margin: 50px;
  min-width: 250px;
}
h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>

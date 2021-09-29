<template>
  <div class="message-container">
    <p>{{ msg }}</p>
  </div>
</template>
<script>
export default {
  name: "Message",
  props: {
    msg: String,
  },
};
</script>
<style scoped>
.message-container {
  color: #004085;
  background-color: #cce5ff;
  border: 2px solid #b8daff;
  border-radius: 5px;
  padding: 0.625rem;
  max-width: 25rem;
  margin: 1.875rem auto;
}
</style>


<template>
  <div id="app">
    <div class="grid">
      <Box />
      <Box />
      <Box />
      <Box />
      <Box />
      <Box />
    </div>
  </div>
</template>

<script>
import Box from "./components/Box";

export default {
  name: "App",
  components: {
    Box,
  },
};
</script>

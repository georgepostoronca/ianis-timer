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

<style>
@charset "UTF-8";
html,
body {
  width: 100%;
  height: 100%;
}

#app {
  width: inherit;
  height: inherit;
}

.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  grid-gap: 10px;
  width: inherit;
  height: inherit;
  counter-reset: section;
}

.box {
  width: 100%;
  height: 100%;
  display: flex;
  align-content: center;
  justify-content: center;
  box-sizing: border-box;
  position: relative;
}
.box:after {
  counter-increment: section;
  /* Инкрементирует счётчик*/
  content: counter(section);
  background-color: #fff;
  position: absolute;
  top: 0;
  left: 0;
  padding: 5px;
  font-family: sans-serif;
}
.box__item {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: #f2f2f2;
  padding: 10px;
  box-sizing: border-box;
}
.box__ready {
  background-color: green;
}
.box input {
  width: 100%;
  height: 40px;
  border: 1px solid #000;
  outline: 0px solid #000;
  padding: 0 10px;
  font-size: 18px;
  box-sizing: border-box;
  width: 100%;
  margin: 10px auto;
}
.box input:focus {
  outline: 2px solid #000;
}

h2 {
  font-size: 30px;
  margin-top: 0;
  margin-bottom: 5px;
}

h3 {
  margin-top: 0;
  margin-bottom: 5px;
  word-break: break-all;
}

.loadding {
  width: 100%;
  height: 10px;
}

input {
  width: 100%;
  height: 40px;
  border: 1px solid #000;
  outline: 0px solid #000;
  padding: 0 10px;
  font-size: 18px;
  box-sizing: border-box;
}
input:focus {
  outline: 2px solid #000;
}

.btn {
  padding: 8px 15px;
  border-radius: 5px;
  border: 0;
  color: #ffffff;
  cursor: pointer;
  background: green;
  transition: 0.2s;
  margin-bottom: 5px;
}
.btn--blue {
  background: blue;
}
.btn--red {
  background: red;
}
</style>

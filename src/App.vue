<template>
  <div id="app">
    <CustomList/>
  </div>
</template>

<script>
import CustomList from "./components/CustomList";

export default {
  name: "App",
  components: {
    CustomList
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

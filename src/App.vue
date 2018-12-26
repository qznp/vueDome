<template>
  <div id="app">
    <ShoppingMall/>
  </div>
</template>

<script>
import ShoppingMall from "./components/pages/ShoppingMall";

export default {
  name: "App",
  components: {
    ShoppingMall
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
}
</style>

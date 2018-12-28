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
  background-color: #f0f0f0;
}
</style>

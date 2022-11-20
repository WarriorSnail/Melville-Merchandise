<template>
  <Navigation/> <!-- calling the 2 components--> 
  <thing/>
</template>

<script>
import thing from './components/thing.vue'
import Navigation from "./components/Navigation.vue";

export default {
  name: 'app',
  components: {
    thing,
    Navigation
  }
}

</script>

<style>/*just some styling */

  * {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: "Raleway", sans-serif;
  font-weight: 400;
}

.app {
  min-height: 100vh;
  position: relative;
  background-color: #f1f1f1;
}
.container {
  padding: 0 20px;
  max-width: 1140px;
  margin: 0 auto;
}
</style>

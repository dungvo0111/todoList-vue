<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>
<script>
import Header from "./components/Header.vue"
export default {
  components: {
    Header
  }
}
</script>
<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

p {
  font-size: 1.2rem;
}
</style>

<template>
  <div class="headerWrapper">
    <h1>Todo List</h1>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.headerWrapper {
  background-color: black;
  color: white;
  padding: 20px 0;
  text-align: center;
}

.headerWrapper a {
    color: white;
    text-decoration: none;
}

.headerWrapper a:hover {
    color: rgb(165, 164, 164)
}
</style>

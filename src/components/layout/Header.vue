<template>
  <header>
    <h1>TodoList</h1>
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
  </header>
</template>

<script>
  export default {
    name: "Header"
  }
</script>

<style scoped>
  header {
    background: gray;
    color: white;
    text-align: center;
    padding: 10px;
  }
</style>

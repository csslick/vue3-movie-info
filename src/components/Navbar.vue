<template>
  <nav>
    <a href="#">Home</a>
    <a href="#">Movies</a>
    <a href="#">About</a>
  </nav>
</template>

<script>
export default {
  name: 'AppNavbar',
}
</script>

<style>
  nav {
    width: 100%;
    background: #000;
    padding: 20px;
    display: flex;
    justify-content: center;
    gap: 2em;
  }
  nav a {
    text-decoration: none;
    color: #fff;
  }
</style>
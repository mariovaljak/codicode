<template>
  <nav>
    <router-link to="/">Home</router-link>
    <router-link to="/history">History</router-link>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  margin: 0 10px;
}

nav a.router-link-exact-active {
  color: white;
  background: #b8860b;
  padding: 5px;
}

body {
  background-image: linear-gradient(to right, #0f0c29, #302b63, #24243e);
}
</style>

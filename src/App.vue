<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style>
html, body {
  background-color: #2c3e50;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ecf0f1;
  background-color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #ecf0f1;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>

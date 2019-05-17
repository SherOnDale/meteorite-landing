<template>
  <div id="app">
    <app-header/>
    <search-bar/>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader";
import SearchBar from "./components/SearchBar";
export default {
  name: "app",
  components: {
    AppHeader,
    SearchBar
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

html {
  font-size: 16px;
}

body {
  background-color: black;
  margin: 0;
}

* {
  box-sizing: border-box;
}
</style>

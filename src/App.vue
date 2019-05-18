<template>
  <div id="app">
    <app-header/>
    <search-bar @click="setSearchKey"/>
    <app-table :search-key="searchKey"/>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader";
import SearchBar from "./components/SearchBar";
import AppTable from "./components/AppTable";
export default {
  name: "app",
  components: {
    AppHeader,
    SearchBar,
    AppTable
  },
  data() {
    return {
      searchKey: ""
    };
  },
  methods: {
    setSearchKey(value) {
      this.searchKey = value;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
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

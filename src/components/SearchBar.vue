<template>
  <div class="search">
    <div class="search__input">
      <input placeholder="Enter search terms">
    </div>
    <div class="search__button">
      <button>Search</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "search-bar"
};
</script>

<style lang="scss" scoped>
.search {
  background-color: #fff;
  padding: 1rem;
  margin: 1rem;
  display: inline-flex;

  .search__input input {
    height: 2rem;
    outline: none;
    border: none;
    border-bottom: 1px solid gray;
    font-size: 0.8rem;
  }

  .search__button button {
    text-transform: uppercase;
    background-color: #7a86cb;
    color: black;
    font-size: 0.8rem;
    padding: 0.4rem 0.8rem;
    margin-left: 1rem;
    outline: none;
    cursor: pointer;
  }
}
</style>


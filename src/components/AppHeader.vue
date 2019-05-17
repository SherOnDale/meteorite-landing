<template>
  <header class="header">
    <h1 class="header__title">Meteorite Explorer</h1>
  </header>
</template>

<script>
export default {
  name: "app-header"
};
</script>

<style scoped lang="scss">
.header {
  background-color: royalblue;

  &__title {
    margin: 0;
    padding: 0.5rem;
    color: white;
  }
}
</style>

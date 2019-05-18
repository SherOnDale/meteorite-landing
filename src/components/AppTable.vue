<template>
  <div class="table__container">
    <div class="table">
      <table-row header/>
      <table-row v-for="item in filteredData" :data="item" :key="item.id"/>
    </div>
  </div>
</template>

<script>
import TableRow from "./TableRow";
export default {
  name: "app-table",
  components: {
    TableRow
  },
  props: {
    searchKey: {
      type: String,
      default: ""
    }
  },
  mounted() {
    fetch("https://data.nasa.gov/resource/gh4g-9sfh.json")
      .then(res => res.json())
      .then(json => {
        this.data = json;
      });
  },
  data() {
    return {
      data: []
    };
  },
  computed: {
    filteredData() {
      const searchKeyRegex = new RegExp(this.searchKey, "i");
      return this.data.filter(item => searchKeyRegex.test(item.name));
    }
  }
};
</script>

<style lang="scss" scoped>
.table {
  width: 90vw;
  margin: 0 auto;
}
</style>

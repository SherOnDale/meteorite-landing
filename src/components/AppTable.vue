<template>
  <div class="table__container">
    <div class="table">
      <table-row header/>
      <table-row v-for="item in filteredData" :data="item" :key="item.id"/>
    </div>
  </div>
</template>

<script>
import data from "../assets/data.json";
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
  data() {
    return {
      data
    };
  },
  computed: {
    filteredData() {
      const searchKeyRegex = new RegExp(this.searchKey, "i");
      console.log(searchKeyRegex);
      return data.filter(item => searchKeyRegex.test(item.name));
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

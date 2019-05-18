<template>
  <div class="table__container">
    <div class="table" v-if="responseLoaded">
      <table-row header/>
      <table-row v-for="item in filteredData" :data="item" :key="item.id"/>
    </div>
    <div class="status" v-else>{{statusMessage}}</div>
  </div>
</template>

<script>
import TableRow from "./TableRow";
import { setTimeout } from "timers";
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
    this.fetchWithTimeout("https://data.nasa.gov/resource/gh4g-9sfh.json")
      .then(res => res.json())
      .then(json => {
        this.data = json;
        this.responseLoaded = true;
      })
      .catch(error => {
        this.statusMessage =
          error.message === "timeout"
            ? "Connection timed out."
            : "Error fetching data.";
        this.statusMessage += " Please try again later";
      });
  },
  data() {
    return {
      data: [],
      responseLoaded: false,
      statusMessage: "Fetching Data..."
    };
  },
  computed: {
    filteredData() {
      const searchKeyRegex = new RegExp(this.searchKey, "i");
      return this.data.filter(item => searchKeyRegex.test(item.name));
    }
  },
  methods: {
    fetchWithTimeout(url) {
      return new Promise((res, rej) => {
        fetch(url).then(res, rej);
        setTimeout(rej, 5000, new Error("timeout"));
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.table {
  width: 90vw;
  margin: 0 auto;
}

.status {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
}
</style>

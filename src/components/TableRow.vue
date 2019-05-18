<template>
  <div class="row row__header" v-if="header">
    <div class="row__field">Name</div>
    <div class="row__field">ID</div>
    <div class="row__field">Name Type</div>
    <div class="row__field">Rec Class</div>
    <div class="row__field">Mass (g)</div>
    <div class="row__field">Fall</div>
    <div class="row__field">Year</div>
    <div class="row__field">Latitude</div>
    <div class="row__field">Longitude</div>
  </div>
  <div class="row" v-else>
    <div class="row__field">{{data.name}}</div>
    <div class="row__field right-align">{{data.id}}</div>
    <div class="row__field">{{data.nametype}}</div>
    <div class="row__field">{{data.recclass}}</div>
    <div class="row__field right-align">{{data.mass}}</div>
    <div class="row__field">{{data.fall}}</div>
    <div
      class="row__field right-align"
    >{{data.year ? $options.filters.formatYear(data.year) : 'N/A'}}</div>
    <div
      class="row__field right-align"
    >{{data.geolocation ? $options.filters.formatCoordinates(data.geolocation.latitude) : 'N/A'}}</div>
    <div
      class="row__field right-align"
    >{{data.geolocation ? $options.filters.formatCoordinates(data.geolocation.longitude): 'N/A'}}</div>
  </div>
</template>

<script>
export default {
  name: "table-row",
  props: {
    header: {
      type: Boolean,
      default: false
    },
    data: {
      type: Object,
      default: () => {}
    }
  },
  filters: {
    formatYear(string) {
      return string.substr(0, 4);
    },
    formatCoordinates(number) {
      return Number(number).toFixed(6);
    }
  }
};
</script>

<style lang="scss" scoped>
.row {
  display: grid;
  padding: 0.6rem 1rem;
  background-color: #fff;
  grid-template-columns: 2fr 1fr 2fr 2fr 1fr 1fr 1fr 2fr 2fr;
  text-align: left;
  grid-gap: 3rem;
  border-bottom: 1px solid #ccc;
}

.row:nth-child(even) {
  background-color: #eee;
}

.row.row__header {
  background-color: orange;
  font-weight: 600;
}

.right-align {
  text-align: right;
}
</style>

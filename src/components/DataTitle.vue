<template>
  <div class="info-title-container">
    <div class="title">{{ text }}</div>
    <div class="date">{{ timestamp }}</div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "DataTitle",
  props: ["text", "dataDate"],
  computed: {
    timestamp: function() {
      return moment(this.dataDate).format("MMMM Do YYYY, h:mm:ss");
    },
  },
};
</script>

<style lang="scss" scoped>
.info-title-container {
  margin-bottom: 1rem;
  .title {
    font-size: 1.4rem;
    font-weight: 600;
  }
}
</style>

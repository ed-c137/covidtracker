<template>
  <div class="stats-container">
    <h3>Cases</h3>
    <div class="">
      <span>New:</span>
      {{ numwcommas(stats.NewConfirmed) }}
    </div>
    <div class="">
      <span>Total:</span>
      {{ numwcommas(stats.TotalConfirmed) }}
    </div>
  </div>
  <div class="stats-container">
    <h3>Deaths</h3>
    <div class="">
      <span>New:</span>
      {{ numwcommas(stats.NewDeaths) }}
    </div>
    <div class="">
      <span>Total:</span>
      {{ numwcommas(stats.TotalDeaths) }}
    </div>
  </div>
</template>

<script>
export default {
  name: "DataBoxes",
  props: ["stats"],
  methods: {
    numwcommas(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>

<style lang="scss" scoped>
.stats-container {
  background: lightblue;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  padding: 1rem;
  margin-bottom: 0.6rem;
  h3 {
    font-size: 1.3em;
    color: darkblue;
    font-weight: 600;
    margin: 0;
  }
}
</style>

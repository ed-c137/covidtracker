<template>
  <main class="home" v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />
    <DataBoxes :stats="stats" />
    <CountriesSelect @get-country="getCountryData" :countries="countries" />
    <button @click="clearCountry()" v-if="stats.Country">Reset</button>
  </main>
  <main v-else>
    <div class="loading-wrap">
      <span>Fetching Data ...</span>
      <img :src="loadingImage" alt="Loading" />
    </div>
  </main>
</template>

<script>
// @ is an alias to /src
import DataTitle from "@/components/DataTitle";
import DataBoxes from "@/components/DataBoxes";
import CountriesSelect from "@/components/CountrySelect";

export default {
  name: "Home",
  components: {
    DataTitle,
    DataBoxes,
    CountriesSelect,
  },
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      stats: {},
      countries: [],
      loadingImage: require("../assets/Spinner.gif"),
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();
      return data;
    },
    getCountryData(country) {
      (this.stats = country), (this.title = country.Country);
    },
    async clearCountry() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = "Global";
      this.stats = data.Global;
      this.loading = false;
    },
  },
  async created() {
    const data = await this.fetchCovidData();
    console.log(data);

    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>

<style scoped lang="scss">
.home {
  margin: 1rem;
}
.loading-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  font-size: 1.3em;
  img {
    height: 2em;
  }
}
</style>

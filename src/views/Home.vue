<template>
  <div>
    <v-main v-if="!loading">
      <DataTitle :title="title" :date="date" />
      <DataBoxes :stats="stats" />
      <CountrySelect :countries="countries" @get-country="getCountryData" />
      <v-btn
        color="green"
        class="rounded-lg white--text"
        v-if="stats.Country"
        @click="clearData"
        >Clear country</v-btn
      >
    </v-main>
    <v-main v-else>
      <div>Fetch Data</div>
      <v-img :src="loadingImage" />
    </v-main>
  </div>
</template>

<script>
import axios from "axios";
import DataTitle from "../components/DataTitle";
import DataBoxes from "../components/DataBoxes";
import CountrySelect from "../components/CountrySelect";

export default {
  name: "Home",

  components: { DataTitle, DataBoxes, CountrySelect },

  data() {
    return {
      date: "",
      contries: [],
      stats: {},
      loading: true,
      title: "Global",
      loadingImage: require("../assets/loading.gif"),
    };
  },

  methods: {
    async fetchCovidData() {
      const result = await axios.get("https://api.covid19api.com/summary");
      this.countries = result.data.Countries;
      this.date = result.data.Date;
      this.stats = result.data.Global;
      this.loading = false;
    },
    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async clearData() {
      this.loading = true;
      const result = await axios.get("https://api.covid19api.com/summary");
      this.title = "Global";
      this.stats = result.data.Global;
      this.loading = false;
    },
  },

  created() {
    this.fetchCovidData();
  },
};
</script>

<template>
  <div>
    <v-main v-if="!loading">
      <DataTitle :title="title" :date="date" />
    </v-main>
    <v-main v-else>
      <div>Fetch Data</div>
      <v-img :src="loadingImage" />
    </v-main>
  </div>
</template>

<script>
import axios from "axios";
import DataTitle from "../components/DataTitle.vue";

export default {
  name: "Home",

  components: { DataTitle },

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
  },

  created() {
    this.fetchCovidData();
  },
};
</script>

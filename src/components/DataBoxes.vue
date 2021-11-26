<template>
  <v-container>
    <v-row>
      <v-col cols="12" md="6">
        <div class="blue lighten-5 text-center rounded-lg pa-7">
          <h3 class="display-1 blue--text text--darken-4 font-weight-black">
            Cases
          </h3>
          <div class="mt-3 title">
            <span class="font-weight-black">New: </span>
            <span>{{ numberWithCommas(stats.NewConfirmed) }}</span>
          </div>
          <div class="mt-3 title">
            <span class="font-weight-black">Total: </span>
            <span>{{ numberWithCommas(stats.TotalConfirmed) }}</span>
          </div>
        </div>
      </v-col>
      <v-col cols="12" md="6">
        <div class="blue lighten-5 text-center rounded-lg pa-7">
          <h3 class="display-1 blue--text text--darken-4 font-weight-black">
            Deaths
          </h3>
          <div class="mt-3 title">
            <span class="font-weight-black">New: </span>
            <span>{{ numberWithCommas(stats.NewDeaths) }}</span>
          </div>
          <div class="mt-3 title">
            <span class="font-weight-black">Total: </span>
            <span>{{ numberWithCommas(stats.TotalDeaths) }}</span>
          </div>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "DataBoxes",
  props: {
    stats: {
      type: Object,
    },
  },
  methods: {
    numberWithCommas(number) {
      return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>

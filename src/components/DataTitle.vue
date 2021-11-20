<template>
  <div class="text-center">
    <h2 class="display-2 font-weight-bold">{{ title }}</h2>
    <div class="headline mt-4 mb-7">{{ formatingDate }}</div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "DataTitle",
  props: {
    title: { type: String },
    date: { type: String },
  },
  computed: {
    formatingDate() {
      return moment(this.date).format("MMMM Do YYYY, h:mm:ss a");
    },
  },
};
</script>

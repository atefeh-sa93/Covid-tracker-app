<template>
  <v-container>
    <v-select
      v-model="selected"
      :items="countries"
      item-text="Country"
      item-value="ID"
      label="Select a country"
      outlined
      @change="onChange()"
    ></v-select>
  </v-container>
</template>

<script>
export default {
  name: "CountrySelect",
  props: {
    countries: {
      type: Array,
    },
  },
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find((item) => item.ID === this.selected);
      this.$emit("get-country", country);
    },
  },
};
</script>

<template>
  <v-container>
    <v-combobox
      v-model="selected"
      :items="countries"
      item-text="Country"
      item-value="ID"
      label="Select a country"
      outlined
      @change="onChange()"
    ></v-combobox>
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
      selected: {},
    };
  },
  methods: {
    onChange() {
      this.$emit("get-country", this.selected);
    },
  },
};
</script>

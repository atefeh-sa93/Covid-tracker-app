<template>
  <header class="text-center blue darken-4 white--text pa-4 mb-10">
    <div class="display-1 text-md-h3 font-weight-bold mb-3">
      <v-icon color="white" large>mdi-virus-outline</v-icon>
      Covid-19-tracker
    </div>
    <p>
      API by
      <router-link
        to="https://covid19api.com"
        class="blue--text text--lighten-4 text-decoration-none"
        target="_blank"
        >covid19api.com</router-link
      >
    </p>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

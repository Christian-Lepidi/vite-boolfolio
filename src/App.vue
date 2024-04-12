<script>
import axios from "axios";

export default {
  data() {
    return {};
  },

  created() {
    axios.get("http://127.0.0.1:8000/api/projects").then((response) => {
      console.log(response);
    });
  },
};
</script>

<template></template>

<style lang="scss">
@use "/src/scss/general.scss";
</style>

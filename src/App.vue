<script>
import axios from "axios";
import { store, api } from "./store";

export default {
  data() {
    return {
      title: "Boolpress",
      store,
    };
  },

  created() {
    axios.get(api.baseUrl + "projects").then((response) => {
      store.projects = response.data;
    });
  },
};
</script>

<template>
  <h1>{{ title }}</h1>
  <div v-for="project in store.projects">
    <ul>
      <li><strong>Titolo:</strong> {{ project.title }}</li>
      <li><strong>Descrizione:</strong> {{ project.description }}</li>
      <li>
        <strong>Data di pubblicazione:</strong>
        {{ project.date_of_publication }}
      </li>
      <hr />
    </ul>
  </div>
</template>

<style lang="scss">
@use "/src/scss/general.scss";
</style>

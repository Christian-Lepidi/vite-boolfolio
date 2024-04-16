<script>
import axios from "axios";
import { store, api } from "./store";
import AppHeader from "./components/AppHeader.vue";

export default {
  data() {
    return {
      title: "Boolfolio",
      store,
    };
  },

  components: { AppHeader },

  created() {
    axios.get(api.baseUrl + "projects").then((response) => {
      store.projects = response.data;
    });
  },
};
</script>

<template>
  <app-header />
  <div class="container mt-5">
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
  </div>
</template>

<style lang="scss">
@use "/src/scss/general.scss";
</style>

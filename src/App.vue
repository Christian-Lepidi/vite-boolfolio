<script>
import axios from "axios";

export default {
  data() {
    return {
      title: "Boolpress",
      projects: [],
    };
  },

  created() {
    axios.get("http://127.0.0.1:8000/api/projects").then((response) => {
      this.projects = response.data;
    });
  },
};
</script>

<template>
  <h1>{{ title }}</h1>
  <div v-for="project in projects">
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

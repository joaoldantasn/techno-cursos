<template>
  <div>
    <div v-if="loading">
      <page-loading />
    </div>
    <div v-if="api">
      <h1>Cursos</h1>
      <p>{{ api }}</p>
    </div>
  </div>
</template>

<script>
import fetchData from "../mixins/fetchData";
export default {
  name: "cursosView",
  mixins: [fetchData],
  created() {
    this.fetchData("/cursos");
  },
};
</script>

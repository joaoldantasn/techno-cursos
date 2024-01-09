<template>
  <div>
    <div v-if="loading">
      <page-loading />
    </div>
    <div v-if="api">
      <h1>Home</h1>
      <p>{{ api }}</p>
    </div>
  </div>
</template>

<script>
import PageLoading from '../components/PageLoading.vue';
import fetchData from "../mixins/fetchData";
export default {
  name: "HomeView",
  mixins: [fetchData, PageLoading],
  created() {
    this.fetchData("/home");
  },
};
</script>

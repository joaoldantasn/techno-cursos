<template>
  <div>
    <div v-if="loading">
      <page-loading />
    </div>
    <transition>
      <div v-if="api" class="conteudo">
        <div>
          <h1>Sobre a {{ api.titulo }}</h1>
          <p>{{ api.descricao }}</p>
          <router-link class="btn-cursos" tag="button" to="/cursos"
            >Cursos</router-link
          >
          <div>
            <h2>Avaliações</h2>
            <ul>
              <li v-for="avaliacao in api.avaliacoes" :key="avaliacao.nome">
                <p>{{ avaliacao.nome }}</p>
                <p>{{ avaliacao.descricao }}</p>
              </li>
            </ul>
          </div>
        </div>
        <img src="../assets/aprender.png" alt="aprenda Web Design" />
      </div>
    </transition>
  </div>
</template>

<script>
import PageLoading from "../components/PageLoading.vue";
import fetchData from "../mixins/fetchData";
export default {
  name: "HomeView",
  mixins: [fetchData, PageLoading],
  created() {
    this.fetchData("/home");
  },
};
</script>

<style>
.btn-cursos {
  border: none;
  background: #4b8;
  border-radius: 4px;
  color: white;
  cursor: pointer;
  padding: 15px 40px;
  font-size: 1rem;
  margin-top: 10px;
  margin-bottom: 40px;
  box-shadow: 0 4px 2px rgba(0, 0, 0, 0.1);
  font-family: "Avenir", Arial, Helvetica, sans-serif;
}
</style>

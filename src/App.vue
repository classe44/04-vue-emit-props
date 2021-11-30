<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <Header @newSearch="searchPokemon" />
          <Main v-if="noResults == false" :pokemonItem="foundPokemon" />
          <div v-else>Non ci sono risultati</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    Main
  },
  data() {
    return {
      base_url: "https://pokeapi.co/api/v2/",
      foundPokemon: {},
      noResults: true
    };
  },
  mounted() {},
  methods: {
    searchPokemon(name) {
        console.log('App.vue ha ricevuto qualcosa da un evento (newSearch)', name);

        axios.get(`${this.base_url}pokemon/${name}`).then( response => {
            console.log('Risposta API', response);
            this.foundPokemon = response.data;
            this.noResults = false;
        }).catch( error => {
            console.log(error);
            this.noResults = true;
        });
    }
  }
};
</script>

<style lang="scss">
@import "./assets/scss/app.scss";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

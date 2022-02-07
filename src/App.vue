<template>
  <div id="app">
    <div class="search">
      <Logo />
      <Header @filtraAncora="filtrati"/>
    </div>
    <div class="main">
      <Lista :film="movies" :series="tvSeries"/>
    </div>
  </div>
</template>

<script>
import Logo from './components/sections/Logo.vue'
import Lista from './components/sections/Lista.vue'
import Header from './components/Header.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Lista,
    Header,
    Logo
  },
  data() {
      return {
          movies: [],
          tvSeries: [],
          input:"",
      }
  },
  methods: {
      getMovies(){
          axios
              .get('https://api.themoviedb.org/3/search/movie', {
                  params: {
                      api_key:"30177aa288b4dd7d8ea1f04ac288ce2b",
                      query:this.input
                  }
              })
              .then( (risposta) => {
                  // handle success
                  this.movies = risposta.data.results;
              })
              .catch(function (error) {
                  // handle error
                  console.log(error);
              });
      },
      getSeries(){
          axios
              .get('https://api.themoviedb.org/3/search/tv', {
                  params: {
                      api_key:"30177aa288b4dd7d8ea1f04ac288ce2b",
                      query:this.input
                  }
              })
              .then( (response) => {
                  // handle success
                  this.tvSeries = response.data.results;
              })
              .catch(function (error) {
                  // handle error
                  console.log(error);
              });
        },
        filtrati(selected){
            this.input = selected;
            this.getMovies();
            this.getSeries();
        },
  }
}
</script>

<style lang="scss">
  @import './assets/global.scss';
  @import './assets/App.scss';
</style>

<template>
  <div class="main">
    <Input @cerca="filtrati"/>
    <Lista :film="movies" :series="tvSeries"/>
  </div>
</template>

<script>
import Input from './sections/Input.vue'
import Lista from './sections/Lista.vue'
import axios from 'axios'

export default {
    name: 'Main',
    components:{
        Input,
        Lista,
    },
    data() {
        return {
            movies: [],
            tvSeries: [],
            input:"",
        }
    },
    // created(){
    //     this.getMovies();
    // },
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

<style>
    .main{
        padding: 20px;
    }
</style>
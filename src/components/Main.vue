<template>
  <div>
    <Input @cerca="filtrati"/>
    <Lista :films="movies"/>
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
        filtrati(selected){
            this.input = selected;
            this.getMovies();
        },
    }
}
</script>

<style>

</style>
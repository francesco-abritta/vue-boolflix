<template>
  <div>
      
        <h1 v-if="film.length>0">Film</h1>
        <div class="listaFilm">
            <div class="itemFilm" v-for="(elementi,indice) in film" :key="'film'+indice">
                <img class="Found" v-if='elementi.poster_path!=null' :src="linkImg + 'w342/' + elementi.poster_path" alt="">
                <img class="notFound" v-else src="../../assets/img/notfound.jpeg" alt="">
                <div class="infoFilm">
                    <ul>
                        <li>
                            <strong>TITOLO: </strong> {{elementi.title}}
                        </li>
                        <li> 
                            <strong>TITOLO ORIGINALE: </strong> {{elementi.original_title}}
                        </li>
                        <li>
                            <strong>LINGUA: </strong> <img class="lingua" :src="require(`../../assets/img/${getFlag(elementi.original_language)}.png`)" alt="">
                        </li>
                        <li>
                            <strong>STELLE: </strong> 
                            <span v-for="stellina in stelline(elementi.vote_average)" :key="'piena'+stellina"><i class="fas fa-star"></i></span>
                            <span v-for="stellina in (5-stelline(elementi.vote_average))" :key="'vuota'+stellina"><i class="far fa-star"></i></span>
                        </li>
                        <li v-if='elementi.overview!=""'>
                            <strong>OVEVIEW: </strong> {{elementi.overview}}
                        </li>
                    </ul>
                </div>
            </div>
        </div>

        <h1 v-if="series.length>0">Serie Tv</h1>
        <div class="listaSerie">
            <div class="itemSerie" v-for="(elements,index) in series" :key="'serie'+index">
                <img class="Found" v-if='elements.poster_path!=null' :src="linkImg + 'w342/' + elements.poster_path" alt="">
                <img class="notFound" v-else src="../../assets/img/notfound.jpeg" alt="">
                <div class="infoSerie">
                    <ul>
                        <li>
                            <strong>TITOLO: </strong> {{elements.name}}
                        </li>
                        <li>
                            <strong>TITOLO ORIGINALE: </strong> {{elements.original_name}}
                        </li>
                        <li>
                            <strong>LINGUA: </strong> <img class="lingua" :src="require(`../../assets/img/${getFlag(elements.original_language)}.png`)" alt="">
                        </li>
                        <li>
                            <strong>STELLE: </strong>
                            <span v-for="stella in stelline(elements.vote_average)" :key="'piena'+stella"><i class="fas fa-star"></i></span>
                            <span v-for="stella in (5-stelline(elements.vote_average))" :key="'vuota'+stella"><i class="far fa-star"></i></span>
                        </li>
                        <li v-if='elements.overview!=""'>
                            <strong>OVEVIEW: </strong> {{elements.overview}}
                        </li>
                    </ul>
                </div>
            </div>
        </div>

  </div>
</template>

<script>
export default {
    name: 'Lista',
    data(){
        return{
            linkImg: "https://image.tmdb.org/t/p/"
        }
    },
    props:{
        film :Array,
        series :Array
    },
    methods: {
        stelline:function(voto){
            return Math.ceil(voto/2);
        },
        getFlag: function(language){
            let urlFlag = "other";
            if(['it','en','es'].includes(language)){
                urlFlag = language;
            }
            return urlFlag;
        }
    }
}
</script>

<style scoped>
  @import '../../assets/Lista.scss';
</style>
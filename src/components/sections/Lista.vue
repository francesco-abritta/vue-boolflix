<template>
  <div>
      <div class="lista">
            <h1 v-if="film.length>0">Film</h1>
            <ul v-for="(elementi,indice) in film" :key="indice">
                <li>TITOLO: {{elementi.title}}</li>
                <li>TITOLO ORIGINALE: {{elementi.original_title}}</li>
                <li>
                    LINGUA: 
                    <img v-if="elementi.original_language == 'it'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/2560px-Flag_of_Italy.svg.png" alt="">
                    <img v-else-if="elementi.original_language == 'en'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/640px-Flag_of_the_United_Kingdom.svg.png" alt="">
                    <img v-else-if="elementi.original_language == 'es'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Flag_of_Spain.svg/1024px-Flag_of_Spain.svg.png" alt="">
                    <img v-else src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/International_Flag_of_Planet_Earth.svg/1280px-International_Flag_of_Planet_Earth.svg.png" alt="">
                </li>
                <li>VOTO: {{elementi.vote_average}}</li>
            </ul>

            <h1 v-if="series.length>0">Serie Tv</h1>
            <ul v-for="(elements,index) in series" :key="index">
                <li>TITOLO: {{elements.name}}</li>
                <li>TITOLO ORIGINALE: {{elements.original_name}}</li>
                <li>
                    LINGUA: 
                    <img v-if="elements.original_language == 'it'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/2560px-Flag_of_Italy.svg.png" alt="">
                    <img v-else-if="elements.original_language == 'en'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/640px-Flag_of_the_United_Kingdom.svg.png" alt="">
                    <img v-else-if="elements.original_language == 'es'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Flag_of_Spain.svg/1024px-Flag_of_Spain.svg.png" alt="">
                    <img v-else src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/International_Flag_of_Planet_Earth.svg/1280px-International_Flag_of_Planet_Earth.svg.png" alt="">
                </li>
                <li>VOTO: {{elements.vote_average}}</li>
            </ul>

      </div>
  </div>
</template>

<script>
export default {
    name: 'Lista',
    props:{
        film :Array,
        series :Array
    }
}
</script>

<style>
    ul{
        margin-bottom: 20px;
    }

    img{
        height: 10px;
        width: 15px;
    }
</style>
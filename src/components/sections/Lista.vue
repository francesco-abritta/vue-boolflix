<template>
  <div>
      <div class="lista">
            <ul>
                <li v-for="(elementi,indice) in films" :key="indice">
                    {{elementi.title}} , 
                    {{elementi.original_title}} , 
                    {{elementi.original_language}} , 
                    {{elementi.vote_average}}
                </li>
            </ul>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Lista',
    props:{
        films :Array
    }
}
</script>

<style>

</style>
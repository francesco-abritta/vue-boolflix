<template>
  <div>
      <input type="text" v-model="inputSearch">
      <button>Cerca</button>
      <div class="lista">
          <ul>
              <li v-for="elementi in 4" :key="elementi">ciao</li>
          </ul>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Input',

}
</script>

<style>

</style>
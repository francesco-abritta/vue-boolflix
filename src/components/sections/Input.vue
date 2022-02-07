<template>
  <div>
      <input placeholder="Digita la tua ricerca" type="text" v-model="inputSearch">
      <button @click="$emit('cerca', inputSearch), svuota()">Cerca</button>
  </div>
</template>

<script>
export default {
    name: 'Input',
    data() {
        return{
            inputSearch:"",
        }
    },
    methods:{
        svuota(){
            this.inputSearch="";
        }
  }
}
</script>

<style scoped>
  @import '../../assets/Input.scss';
</style>
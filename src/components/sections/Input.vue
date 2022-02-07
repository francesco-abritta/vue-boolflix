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
    input{
        padding: 10px;
        border: 0;
        border-radius: 10px;
        margin-right: 10px;
    }
    button{
        padding: 10px;
        border-radius: 10px;
        border: 0;
        background-color: black;
        color: white;
        cursor: pointer;
    }
    button:hover{
        background-color: white;
        color: black;
    }
</style>
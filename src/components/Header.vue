<template>
  <div>
    <Input @cerca="passaFiltro"/>
  </div>
</template>

<script>
import Input from './sections/Input.vue'
export default {
    name: 'Header',
    components: {
        Input
    },
    methods: {
        passaFiltro(inputFiltro) {
            this.$emit('filtraAncora',inputFiltro);
        }
    }
}
</script>

<style>

</style>
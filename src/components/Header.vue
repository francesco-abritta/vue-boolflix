<template>
  <div class="top">
    <Logo />
    <Input @cerca="passaFiltro"/>
  </div>
</template>

<script>
import Input from './sections/Input.vue'
import Logo from './sections/Logo.vue'
export default {
    name: 'Header',
    components: {
        Input,
        Logo
    },
    methods: {
        passaFiltro(inputFiltro) {
            this.$emit('filtraAncora',inputFiltro);
        }
    }
}
</script>

<style scoped>
  .top{
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>
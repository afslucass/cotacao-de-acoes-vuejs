<template>
  <div>
    <barra-de-pesquisa v-on:EnviarRequestDeAcao='this.acao = $event' />
    <container-acoes v-bind:acaoParaEnviarRequest='acao' />
  </div>
</template>

<script>
import BarraDePesquisa from './components/BarraDePesquisa.vue'
import ContainerAcoes from './components/ContainerAcoes.vue'

export default {
  name: 'App',
  components: {
    BarraDePesquisa,
    ContainerAcoes
  },
  data() {
    return {
      acao: ''
    }
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto+Slab&display=swap');

  html, body {
    margin: 0px;
    padding: 0px;

    box-sizing: border-box;
    
    background-color: hsl(0, 0%, 93%);

    font-family: 'Roboto Slab', serif;
  }
</style>

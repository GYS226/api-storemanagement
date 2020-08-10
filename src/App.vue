<template>
  <div id="app">
    <composante :msg="imgsrc"/>
  </div>
</template>

<script>
import Composante from './components/compt1.vue'

export default {
  name: 'App',
  components: {
    Composante
  },
  data(){
    return{
      // ceci est un v-bind, on met me texte dans une variable
      imgsrc:'https://picsum.photos/id/1/200/300'
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
  <div id="app">
    <a :href="'http://lorempicsum.com/futurama/800/600/' + n" v-lightbox v-for="n in 9" :key="n">
      <img :src="'http://lorempicsum.com/futurama/150/150/' + n"/>
    </a>
    <a :href="'http://lorempicsum.com/nemo/800/600/' + n" v-lightbox="'nemo'" v-for="n in 9" :key="'nemo' + n">
      <img :src="'http://lorempicsum.com/nemo/150/150/' + n"/>
    </a>
    <lightbox></lightbox>
  </div>
</template>

<script>
import Lightbox from './components/lightbox/Lightbox'

export default {
  name: 'App',
  components: {
    Lightbox
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

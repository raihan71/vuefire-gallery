<template>
  <div id="app">
    <Gallery />
    <ButtonUpload />
  </div>
</template>

<script>
import Gallery from './components/Gallery.vue';
import ButtonUpload from './components/ButtonUpload.vue';
export default {
  name: 'App',
  components: {
    Gallery,
    ButtonUpload
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

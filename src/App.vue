<template>
  <Header />
  <Footer />
</template>

<script>

import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap/dist/js/bootstrap.js'
import Header from './components/partials/Header.vue';
import Footer from './components/partials/Footer.vue';


export default {
  name: 'App',
  components: {
    Header,
    Footer
  }
}
</script>

<style type="scss">
* {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
  <Header />
  <main>
    <BannerSection />
  </main>
  <Footer />
</template>

<script>

import Header from './components/partials/Header.vue';
import Footer from './components/partials/Footer.vue';

// BANNER
import BannerSection from './components/layout/BannerSection.vue';


import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap/dist/js/bootstrap.js'


export default {
  name: 'App',
  components: {
    Header,
    Footer,
    BannerSection
  }
}
</script>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700;800;900&display=swap');

* {
  margin: 0;
  padding: 0;
  font-family: 'Montserrat', sans-serif;
}

.container {
  @media all and (min-width: 1480px) {
    max-width: 1640px;
  }
}


</style>

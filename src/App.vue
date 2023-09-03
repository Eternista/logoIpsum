<template>
  <Header />
  <main>
    <BannerSection id="home" />
    <AboutSection id="about" />
    <GallerySection id="gallery" />
  </main>
  <Footer />
</template>

<script>

import Header from './components/partials/Header.vue';
import Footer from './components/partials/Footer.vue';

// BANNER
import BannerSection from './components/layout/BannerSection.vue';
import AboutSection from './components/layout/AboutSection.vue';
import GallerySection from './components/layout/GallerySection.vue';


import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap/dist/js/bootstrap.js'


export default {
  name: 'App',
  components: {
    Header,
    Footer,
    BannerSection,
    AboutSection,
    GallerySection
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

main {
  padding-top: 100px;
}

.container {
  @media all and (min-width: 1480px) {
    max-width: 1640px;
  }
}

.title {
  text-align: left;
  font-weight: 900;
  font-size: 48px;
  line-height: 57px;
  letter-spacing: 19.2px;
  margin-bottom: 45px;
  &__separator {
    display: block;
    margin-top: 30px;
    background-color: #FF4359;
    height: 2px;
    width: 100%;
  }
  &.centred {
    text-align: center;
    display: block;
    width: fit-content;
    margin: 0 auto;
  }
}


</style>

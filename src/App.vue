<template>
  <Header />
  <main>
    <BannerSection id="start" />
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

#app, body, html {
  overflow-x: hidden;
}

main {
  padding-top: 100px;
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
    margin: 0 auto 70px;
  }
  @media all and (max-width: 1180px) {
    font-size: 36px;
    line-height: 45px;
    margin-bottom: 30px;
    .title__separator {
      margin-top: 15px;
    }
    &.centred {
      margin: 0 auto 45px;
    }
  }
}


</style>

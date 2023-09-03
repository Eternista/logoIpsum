<template>
  <section :id="id" class="l-sec l-sec--banner">
    <picture >
        <!-- DESKTOP IMAGE -->
        <source media="(min-width: 1180px)" :srcset="desktop" />
        <!-- Tablet IMAGE -->
        <source media="(min-width: 768px) and (max-width: 1179px)" :srcset="tablet" />
        <!-- Mobile IMAGE -->
        <source media="(min-width: 1px) and (max-width: 767px)" :srcset="mobile" />
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFCAYAAACNbyblAAAAHElEQVQI12P4
        //8/w38GIAXDIBKE0DHxgljNBAAO9TXL0Y4OHwAAAABJRU5ErkJggg==" alt="Red dot" />
    </picture>
  </section>
</template>
  

<script>
  import Desktop from '@/assets/banner/desktop.jpg';
  import Tablet from '@/assets/banner/tablet.jpg';
  import Mobile from '@/assets/banner/mobile.jpg';

  export default {
    props: {
      id: String
    },
    data() {
      return {
        desktop: Desktop,
        tablet: Tablet,
        mobile: Mobile
      }
    },
  };
  </script>
  
  <style lang="scss" scoped>

    .l-sec--banner {

      margin-bottom: 220px;

      picture {
        img {
          max-width: 100%;
          object-fit: cover;
          object-position: center;
          height: 813px;
          @media all and (max-width: 1179px) {
            height: 500px;
          }
          @media all and (max-width: 767px) {
            height: 325px;
          }
        }
      }
    }

  </style>
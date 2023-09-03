<template>
    <section :id="id" class="l-sec l-sec--gallery">
        <div class="container-fluid">
            <div class="row">
                <div class="col-12">
                    <h2 class="title centred">Galeria <span class="title__separator short"></span></h2>
                </div>
            </div>
        </div>
    </section>
  </template>
    
  
  <script>

    import AboutImage from "@/assets/about-me.jpg";

    export default {
    props: {
      id: String
    },
      data() {
        return {
            slides: AboutImage,
        }
      },
    };
    </script>
    
    <style lang="scss">
        .l-sec--gallery {
            padding: 55px 0;
            .container-fluid {
                max-width: 1360px;
            }
        }
    </style>
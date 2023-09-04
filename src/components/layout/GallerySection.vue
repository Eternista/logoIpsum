<template>
    <section :id="id" class="l-sec l-sec--gallery">
        <div class="container-fluid">
            <div class="row">
                <div class="col-12">
                    <h2 class="title centred">Galeria <span class="title__separator short"></span></h2>
                    <swiper
                        :modules="modules"
                        :slides-per-view="1"
                        :space-between="100"
                        navigation
                        :pagination="{ clickable: true }"
                        @swiper="onSwiper"
                        @slideChange="onSlideChange"
                    >
                        <swiper-slide v-for="(slide, index) in slides" :key="index">
                            <img :src="slide.src" />
                        </swiper-slide>
                    </swiper>
                </div>
            </div>
        </div>
    </section>
  </template>
    
  
  <script>

    // SLIDER IMAGES

    import Slide1 from "@/assets/gallery/slide-1.jpg";
    import Slide2 from "@/assets/gallery/slide-2.jpg";
    import Slide3 from "@/assets/gallery/slide-3.jpg";
    import Slide4 from "@/assets/gallery/slide-4.jpg";


    // SWIPER UPDATE
    
    import { Navigation, Pagination} from 'swiper/modules';
    import { Swiper, SwiperSlide } from 'swiper/vue';

    import 'swiper/css';
    import 'swiper/css/navigation';
    import 'swiper/css/pagination';

    //END OF SWIPER

    export default {
      props: {
        id: String
      },
      data() {
        return {
            slides: [
                {
                    src: Slide1
                },
                {
                    src: Slide2
                },
                {
                    src: Slide3
                },
                {
                    src: Slide4
                }
            ],
        }
      },
      components: {
        Swiper,
        SwiperSlide,
        },
        setup() {
            return {
                modules: [Navigation, Pagination],
            };
        },
    };
    </script>
    
    <style lang="scss">
        .l-sec--gallery {
            padding: 55px 0;
            .container-fluid {
                max-width: 1365px;
                width: 100%;
                .col-12 {
                    padding: 0 !important;
                    .swiper {
                        overflow: unset;
                        margin-bottom: 54px;
                        .swiper-slide {
                            opacity: 1;
                            transition: .4s ease;
                            img {
                                max-width: 100%;
                            }
                        }
                        .swiper-slide:not(.swiper-slide-active) {
                            opacity: .2;

                        }
                    }
                    .swiper-button-next, .swiper-button-prev  {
                        color: #FF4359;
                        font-weight: 900;
                        &.swiper-button-disabled {
                            opacity: 1;
                            color: #AFAFAF;
                        }
                    }
                    .swiper-button-next {
                        left: calc(100% + 15px);
                        right: unset;
                    }
                    .swiper-button-prev {
                        left: unset;
                        right: calc(100% + 15px);
                    }
                    .swiper-pagination {
                        top: calc(100% + 30px);
                        bottom: unset;
                        display: flex;
                        justify-content: center;
                        align-items: center;
                        .swiper-pagination-bullet {
                            height: 18px;
                            width: 18px;
                            transition: .4s ease;
                            &:hover, &.swiper-pagination-bullet-active {
                                background-color: #FF4359;
                            }
                            &.swiper-pagination-bullet-active {
                                height: 24px;
                                width: 24px;
                            }
                        }
                    }
                }
            }
        }
    </style>
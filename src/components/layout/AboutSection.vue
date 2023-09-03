<template>
    <section :id="id" class="l-sec l-sec--about">
        <div class="container-fluid">
            <div class="row">
                <div class="col col--image">
                    <img :src="image" alt="O mnie zdjęcie" />
                </div>
                <div class="col col--text">
                    <div class="text-container">
                        
                        <h1 class="title">O Mnie <span class="title__separator"></span></h1>
                        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.<br/><br/>
                            Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.<br/><br/>
                            Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt.<br/><br/>
                            Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam.</p>
                    </div>
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
            image: AboutImage,
        }
      },
    };
    </script>
    
    <style lang="scss">
  
        .l-sec--about {
            margin-bottom: 233.5px;
            @media all and (max-width: 1179px) {
                margin-bottom: 55px;
            }
            @media all and (max-width: 767px) {
                margin-bottom: 0px;
            }
            .row {
                align-items: center;
            }
            .col {
                flex: unset;
                &--image {
                    max-width: 1090px;
                    width: 100%;
                    @media all and (max-width: 1770px) {
                        max-width: unset;
                        width: 60%;
                    }
                    @media all and (max-width: 1500px) {
                        width: 50%;
                    }
                    img {
                        margin: 0 calc(-1 * var(--bs-gutter-x) * 0.5);
                        width: calc(100% + (2 * var(--bs-gutter-x) * 0.5));
                        height: 613px;
                        object-fit: cover;
                    }
                    @media all and (max-width: 1180px) {
                        width: 100%;
                        order: 1;
                        img {
                            height: 315px;
                        }
                    }
                }
                &--text {
                    width: calc(100% - 1090px);
                    @media all and (max-width: 1770px) {
                        max-width: unset;
                        width: 40%;
                    }
                    @media all and (max-width: 1500px) {
                        width: 50%;
                    }
                    .text-container {
                        max-width: 536px;
                        width: 100%;
                        margin-left: auto;
                        margin-right: auto;
                        p {
                            font-size: 16px;
                            line-height: 24px;
                            font-weight: 300;
                            letter-spacing: 0px;
                            color: #000000;
                            margin-bottom: 0;
                        }
                    }
                    @media all and (max-width: 1180px) {
                        width: 100%;
                        order: 0;
                        .text-container {
                            max-width: 100%;
                            padding: 0px 30px 55px;
                        }
                    }
                }
            }
        }
  
    </style>
<template>
    <header>
        <div class="container">
            <div class="row" v-if="mobileNavigation == false">
                <div class="col col--menu">
                    <div class="col--menu__logo"><a href="#home"><img :src="logo" alt="logoIpsum"/></a></div>
                    <nav class="col--menu__nav">
                        <ul class="menu">
                            <li class="menu__item"><a class="btn btn--primary" href="#start">Start</a></li>
                            <li class="menu__item"><a class="btn btn--primary" href="#about">O Mnie</a></li>
                            <li class="menu__item"><a class="btn btn--primary" href="#galeria">Galeria</a></li>
                            <li class="menu__item"><button class="btn btn--primary" @click="showModal = true">Kontakt</button></li>
                        </ul>
                    </nav>
                </div>
                <div class="col col--social">
                    <nav class="social-menu">
                        <ul class="menu">
                            <li :class="'menu__item social ' + 'social--' + item.alt" v-for="(item, index) in icons" :key="index">
                                <a :href="item.url">
                                    <img :src="item.src" :alt="item.alt"/>
                                </a>
                            </li>
                        </ul>
                    </nav>
                </div>
            </div>
            <div class="row" v-if="mobileNavigation == true">
                <div class="col col--mobile">
                    <div class="col--mobile__logo"><a href="#home"><img :src="logo" alt="logoIpsum"/></a></div>
                    <nav class="col--mobile__nav">
                        <ul class="menu">
                            <li class="menu__item"><a class="btn btn--mobile" href="#start">Start</a></li>
                            <li class="menu__item"><a class="btn btn--mobile" href="#about">O Mnie</a></li>
                            <li class="menu__item"><a class="btn btn--mobile" href="#galeria">Galeria</a></li>
                            <li class="menu__item"><button class="btn btn--mobile" @click="showModal = true">Kontakt</button></li>
                        </ul>
                    </nav>
                    <nav class="social-menu">
                        <ul class="menu">
                            <li :class="'menu__item social ' + 'social--' + item.alt" v-for="(item, index) in icons" :key="index">
                                <a :href="item.url">
                                    <img :src="item.src" :alt="item.alt"/>
                                </a>
                            </li>
                        </ul>
                    </nav>
                </div>
            </div>
        </div>
    </header>
    <Modal :showModal="showModal" @close-modal="showModal = false" />
</template>

<style lang="scss">
    header {
        padding: 23px 0;
        border-bottom: 4px solid #FF4359;
        position: fixed;
        width: 100%;
        background-color: #fff;
        top: 0;
        left: 0;
        .container {
            .row {
                justify-content: space-between;
                align-items: center;
                .col {
                    flex: unset;
                    &--menu {
                        max-width: 944px;
                        width: 100%;
                        display: flex;
                        align-items: center;
                        &__logo {
                            margin-right: 60px;
                        }
                    }
                    &--social {
                        width: 134px;
                        .social {
                            transform: scale(1);
                            transition: .4s ease;
                            &:hover {
                                transform: scale(1.04);
                            }
                        }
                    }
                }
            }
        }
        .btn {
            padding: 15px 40px;
            border-radius: 21px;
            &--primary {
                text-align: left;
                font: normal normal 300 12px/14px Montserrat;
                letter-spacing: 4.8px;
                color: #AFAFAF;
                text-transform: uppercase;
                opacity: 1;
                box-shadow: 0px 5px 10px rgba(0,0,0,0);
                width: max-content;
                transition: .4s ease;
                &:hover {
                    box-shadow: 0px 5px 10px #FC435933;
                }
            }
        }
    
        .menu {
            display: flex;
            list-style: none;
            margin: 0;
            padding: 0;
            &__item {
                margin-right: 20px;
                &.social {
                    margin-right: 12px;
    
                }
                &:last-child {
                    margin-right: 0 !important;
                }
            }
        }
    }


  </style>
  
  <script>

import Modal from '../layout/ContactModal.vue'; // Import the Modal component
import Logo from '@/assets/logo.png';
import Facebook from '@/assets/facebook.svg';
import Instagram from '@/assets/instagram.svg';
import Youtube from '@/assets/youtube.svg';

  export default {
    name: 'PartialHeader',
    components: {
        Modal, // Register the Modal component
    },
    data() {
        return {
            showModal: false,
            logo: Logo,
            icons: [
                {
                    src: Facebook,
                    url: "#",
                    alt: "facebook"
                },
                {
                    src: Instagram,
                    url: "#",
                    alt: "instagram"
                },
                {
                    src: Youtube,
                    url: "#",
                    alt: "youtube"
                }
            ],
            mobileNavigation: false
        };
        
    },
  }
  </script>
  
  
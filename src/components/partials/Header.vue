<template>
    <header>
        <div class="container-fluid">
            <div class="row">
                <div class="col col--menu">
                    <div class="col--menu__logo"><a href="#home"><img :src="logo" alt="logoIpsum"/></a></div>
                    <nav class="col--menu__nav mobile-none">
                        <ul class="menu">
                            <li class="menu__item"><a class="btn btn--primary" href="#start">Start</a></li>
                            <li class="menu__item"><a class="btn btn--primary" href="#about">O Mnie</a></li>
                            <li class="menu__item"><a class="btn btn--primary" href="#gallery">Galeria</a></li>
                            <li class="menu__item"><button class="btn btn--primary" @click="showModal = true">Kontakt</button></li>
                        </ul>
                    </nav>
                </div>
                <div class="col col--social mobile-none">
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
                <div :class="['hamb desktop-none', menuAct ? 'active' : '']" @click="menuAct = !menuAct">
                    <span class="hamb__line top"></span>
                    <span class="hamb__line middle"></span>
                    <span class="hamb__line bot"></span>
                </div>
            </div>
        </div>
    </header>
    <nav :class="['navigation-mobile desktop-none', menuAct ? 'active' : '']" @click="menuAct = !menuAct">
        <ul class="menu">
            <li class="menu__item"><a class="btn btn--mobile" href="#start">Start</a></li>
            <li class="menu__item"><a class="btn btn--mobile" href="#about">O Mnie</a></li>
            <li class="menu__item"><a class="btn btn--mobile" href="#gallery">Galeria</a></li>
            <li class="menu__item"><button class="btn btn--mobile" @click="showModal = true">Kontakt</button></li>
        </ul>
        <ul class="menu social">
            <li :class="'menu__item social ' + 'social--' + item.alt" v-for="(item, index) in icons" :key="index">
                <a :href="item.url">
                    <img :src="item.src" :alt="item.alt"/>
                </a>
            </li>
        </ul>
    </nav>
    <Modal :showModal="showModal" @close-modal="showModal = false" />
</template>

<style lang="scss">
    header {
        padding: 23px 0;
        border-bottom: 4px solid #FF4359;
        position: fixed;
        z-index: 99;
        width: 100%;
        background-color: #fff;
        top: 0;
        left: 0;
        .container-fluid {
            max-width: 1640px;
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
                        width: 145px;
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
                text-transform: uppercase;
                color: #AFAFAF;
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

        .hamb {
            position: absolute;
            top: 50%;
            right: 15px;
            height: 17px;
            width: 32px;
            transform: translateY(-50%);
            padding: 0;
            z-index: 9999;
            &__line {
                width: 100%;
                height: 3px;
                background-color: #AFAFAF;
                display: block;
                position: absolute;
                transition: .4s ease;
                opacity: 1;
                transform: rotate(0deg);
                &.top {
                    top: 0;
                }
                &.middle {
                    top: 7px;
                }
                &.bot {
                    top: 14px;
                }
            }
            &:hover, &.active {
                .hamb__line {
                    background-color: #FF4359;
                }
            }
            &.active {
                .hamb__line {
                    &.top {
                        transform: rotate(-45deg);
                        width: 16px;
                    }
                    &.bot {
                        transform: rotate(45deg);
                        width: 16px;
                    }
                }
            }
        }

        
    }

    .navigation-mobile {
        position: fixed;
        top: 0;
        right: 0;
        width: 300px;
        display: none;
        height: 100vh;
        z-index: 98;
        border-left: 3px solid #FF4359;
        background-color: #fff;
        padding-top: 130px;
        &.active {
            display: block;
        }
        .menu {
            list-style: none;
            padding: 20px;
            margin: 0;
            &:not(.social) {
                .menu__item {
                    width: 100%;
                    border-bottom: 2px solid #FF4359;
                    margin-bottom: 20px;
                    a, button {
                        font: normal normal 300 12px/14px Montserrat;
                        letter-spacing: 4.8px;
                        text-transform: uppercase;
                        color: #AFAFAF;
                        width: 100%;
                        height: 42px;
                        display: flex;
                        align-items: center;
                        justify-content: center;
                    }
                }
            }
            &.social {
                display: flex;
                width: 100%;
                justify-content: center;
                .menu__item {
                    margin-right: 12px;
                }
            }
        }
    }
    .desktop-none {
        @media all and (min-width: 1180px) {
            display: none;
        }
    }
    .mobile-none {
        @media all and (max-width: 1179px) {
            display: none;
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
            menuAct: false
        };
        
    },
  }
  </script>
  
  
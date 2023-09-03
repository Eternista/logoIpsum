<!-- Modal.vue -->
<template>
    <div class="contact-modal" v-if="showModal">
        <form class="form" :click="(e) => e.preventDefault()">
            <label for="name">
                <p>Imię <span class="red-star">*</span></p>
                <input id="name" type="text" name="name" required placeholder="- wpisz -" />
            </label>
            <label for="surname"></label>
            <label for="email"></label>
        </form>
        <button @click="() => {
            $emit('close-modal');

        }">Close</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      showModal: Boolean, // Boolean prop to control the modal visibility
    }
  };
  </script>
  
  <style lang="scss" scoped>
  .contact-modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    align-items: center;
    justify-content: center;
    display: flex;
    .form {
        box-shadow: 0px 0px 99px #FF4359;
        background-color: #fff;
        padding: 45px 55px;
        max-width: 536px;
        width: 100%;
    }


    }

  </style>
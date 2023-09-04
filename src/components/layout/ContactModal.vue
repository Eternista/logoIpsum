<!-- Modal.vue -->
<template>
    <div class="contact-modal" v-if="showModal">
        <form class="form" :onSubmit="(e) => {submitForm(e)}">
          <div class="form__container">
            <label for="name">
                <p class="desc">Imię <span class="red-star">*</span></p>
                <input id="name" type="text" name="name" :onChange="(e) => {name = e.target.value}" required placeholder="- wpisz -" />
            </label>
            <label for="surname">
              <p class="desc">Nazwisko <span class="red-star">*</span></p>
              <input id="surname" type="text" name="surname" :onChange="(e) => {surname = e.target.value}" required placeholder="- wpisz -" />
            </label>
            <label for="email">
              <p class="desc">Adres E-mail <span class="red-star">*</span></p>
              <input id="email" type="email" name="email" :onChange="(e) => {email = e.target.value}" required placeholder="- wpisz -" />
            </label>
            <p class="break"><span class="red-star">*</span> - pole wymagane</p>
            <label for="check" class="check">
              <input type="checkbox" name="check" required id="check" :onClick="() => {check = !check}" />
              <span :class="['checkbox', check ? 'checked' : '']"></span>
              <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
            </label>
            <button type="submit" class="btn btn--submit">Wyślij</button>
            <span v-if="error" class="error">Proszę uzupełnić wymagane pola!</span>
          </div>
        <span class="close" @click="() => {
            $emit('close-modal');

        }"><img src="@/assets/close.svg" /></span>
        </form>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      showModal: Boolean, // Boolean prop to control the modal visibility
    },
    data() {
      return {
        check: false,
        error: false,
        name: '',
        surname: '',
        email: ''
      }
    },
    methods: {
      submitForm: function (e) {
        e.preventDefault();
        var regex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
        if((this.name.length <= 2 || this.surname.length <= 2 || this.email.length <= 5 || this.check == false) && this.email.test(regex) ) {
          this.error = true;
        } else {
          this.error = false;
          const data = {
            "name": this.name,
            "surname": this.surname,
            "email": this.email,
            "check": this.check
          }
          
          fetch('http://localhost:3000/contactRequest/', {
            method: 'POST',
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify(data)
          }).then(response => {
            if (!response.ok) {
              throw new Error(`HTTP error! Status: ${response.status}`);
            }
            return response.json();
        }).then(responseData => {
            console.log(responseData);
          }).catch(err => {
          console.log(err.message)
        })

        }
      }
    }
  };
  </script>
  
  <style lang="scss" scoped>
  .contact-modal {
    .error {
      text-align: center;
      font: normal normal 300 12px/14px Montserrat;
      letter-spacing: 0px;
      color: #FF4359;
    }
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    align-items: center;
    justify-content: center;
    display: flex;
    z-index: 999;
    .btn {
      padding: 14px 16px;
      width: 100%;
      height: 41px;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      font: normal normal 300 16px/14px Montserrat;
      letter-spacing: 0px;
      transition: .4s ease;
      &--submit {
        background-color: #FF4359;
        color: #FFFFFF;
      }
      border-radius: 6px;
      &:hover {
        letter-spacing: 6.4px;
      }
    }
    .break {
      font: normal normal 400 12px/14px Montserrat;
      letter-spacing: 0px;
      margin-bottom: 15px;
    }

      .desc {
        text-align: left;
        font: normal normal 300 12px/14px Montserrat;
        letter-spacing: 4.8px;
        text-transform: uppercase;
        margin-bottom: 10px;
      }
    input {
      border: 1px solid #AFAFAF;
      border-radius: 6px;
      opacity: 1;
      background-color: #fff;
      padding: 14px 16px;
      width: 100%;
      text-align: left;
      font: normal normal 300 12px/14px Montserrat;
      letter-spacing: 4.8px;
      color: #AFAFAF;
      opacity: 1;
      margin-bottom: 15px;
      &[type="checkbox"] {
        display: none;
      }
    }

    .red-star {
      color: #FF4359;
    }
    .check {
      display: flex;
      gap: 13px;
      margin-bottom: 15px;
      p {
        width: calc(100% - 33px);
        font: normal normal 500 10px/14px "Montserrat" !important;
        letter-spacing: 0px !important;
        color: #000000 !important;
        margin: 0;
      }
    }
    .checkbox {
      height: 20px;
      width: 20px;
      border: 1px solid #AFAFAF;
      border-radius: 6px;
      opacity: 1;
      display: block;
      &.checked {
        background-image: url('@/assets/check.svg');
        background-size: 13px;
        background-repeat: no-repeat;
        background-position: center 5px;
      }
    }
    .form {
        box-shadow: 0px 0px 99px #FF4359;
        background-color: #fff;
        border-radius: 21px;
        padding: 45px 55px;
        max-width: 536px;
        width: 100%;
        display: flex;
        position: relative;
        .close {
          position: absolute;
          top: 24px;
          right: 24px;
          cursor: pointer;
        }
        justify-content: center;
        &__container {
          max-width: 260px;
          width: 100%;
          & > * {
            width: 100%;
          }
        }
    }


    }

  </style>
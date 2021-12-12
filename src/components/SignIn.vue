<template>
  <div class="sign-in__wrapper">
    <div
      class="sign-in__container fadeIn"
      v-show="!signUpShow"
    >
      <h2>Sign into your account</h2>
      <!--===========================================-->
      <!-- ========== Sign In ============ -->
      <form class="sign-in__form" @submit.prevent="submitSignIn">
        <div class="sign-in__input-container">
          <label
          for="emailSignIn"
          class="form__label"
          :class="{
            'form__label-error': v$.signIn.email.$error,
            'form__label-valid': v$.signIn.email.$invalid  === false
          }"
          >
            E-mail
          </label>
          <div class="sign-in__icon_container">
            <div class="sign-in__icon">
              <svg
              class="sign-in__icon"
              width="120"
              height="162"
              viewBox="0 0 120 162"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
              >
                <rect width="120" height="162" fill="white"/>
                <rect :class="{'form__input-error': v$.signIn.email.$error, 'form__input-valid': v$.signIn.email.$invalid  === false}" x="5" y="40" width="110" height="82" rx="5" stroke="black" stroke-width="10"/>
                <line :class="{'form__input-error': v$.signIn.email.$error, 'form__input-valid': v$.signIn.email.$invalid  === false}" x1="13.0058" y1="43.0413" x2="59.0413" y2="77.9942" stroke="black" stroke-width="10" stroke-linecap="round"/>
                <line :class="{'form__input-error': v$.signIn.email.$error, 'form__input-valid': v$.signIn.email.$invalid  === false}" x1="60.9587" y1="77.9942" x2="106.994" y2="43.0413" stroke="black" stroke-width="10" stroke-linecap="round"/>
              </svg>
            </div>
          </div>
          <input
            class="sign-in__input form__input"
            :class="{
              'form__input-error': v$.signIn.email.$error,
              'form__input-valid': v$.signIn.email.$invalid  === false
            }"
            id="emailSignIn"
            name="email"
            type="email"
            autocomplete="on"
            v-model="signIn.email"
            @blur="v$.signIn.email.$touch"
          />
          <span
            class="sign-in__error"
            v-if="v$.signIn.email.$error"
          >
            Enter correct email
          </span>
        </div>
        <div class="sign-in__input-container">
          <label
          for="passSignIn"
          class="form__label"
          :class="{
            'form__label-error': v$.signIn.pass.$error,
            'form__label-valid': v$.signIn.pass.$invalid  === false
          }"
          >
            Password
          </label>
          <div class="sign-in__icon_container">
            <div class="sign-in__icon">
              <svg
              class="sign-in__icon"
              width="120"
              height="162"
              viewBox="0 0 120 162"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
              >
                <rect width="120" height="162" fill="white"/>
                <rect :class="{'form__input-error': v$.signIn.pass.$error, 'form__input-valid': v$.signIn.pass.$invalid  === false}" x="5" y="67" width="110" height="90" rx="5" stroke="black" stroke-width="10"/>
                <path :class="{'form__input-error': v$.signIn.pass.$error, 'form__input-valid': v$.signIn.pass.$invalid  === false}" d="M20 45C20 39.7626 21.0544 34.5737 23.1058 29.7288C25.1574 24.8836 28.1674 20.4739 31.9696 16.7544C35.7719 13.0346 40.292 10.0783 45.2743 8.05944C50.2568 6.04047 55.6007 5 61 5C66.3993 5 71.7432 6.04047 76.7257 8.05943C81.708 10.0783 86.2281 13.0346 90.0304 16.7544C93.8326 20.4739 96.8426 24.8836 98.8942 29.7288C100.946 34.5737 102 39.7626 102 45" stroke="black" stroke-width="10"/>
                <line :class="{'form__input-error': v$.signIn.pass.$error, 'form__input-valid': v$.signIn.pass.$invalid  === false}" x1="20" y1="45" x2="20" y2="62" stroke="black" stroke-width="10"/>
                <line :class="{'form__input-error': v$.signIn.pass.$error, 'form__input-valid': v$.signIn.pass.$invalid  === false}" x1="102" y1="45" x2="102" y2="62" stroke="black" stroke-width="10"/>
                <circle :class="{'form__input-error-icon': v$.signIn.pass.$error, 'form__input-valid-icon': v$.signIn.pass.$invalid  === false}" cx="30" cy="112" r="10" fill="#010101"/>
                <circle :class="{'form__input-error-icon': v$.signIn.pass.$error, 'form__input-valid-icon': v$.signIn.pass.$invalid  === false}" cx="60" cy="112" r="10" fill="#010101"/>
                <circle :class="{'form__input-error-icon': v$.signIn.pass.$error, 'form__input-valid-icon': v$.signIn.pass.$invalid  === false}" cx="90" cy="112" r="10" fill="#010101"/>
              </svg>
            </div>
          </div>
          <input
            class="sign-in__input form__input"
            :class="{
              'form__input-error': v$.signIn.pass.$error,
              'form__input-valid': v$.signIn.pass.$invalid  === false
            }"
            id="passSignIn"
            name="pass"
            type="password"
            autocomplete="on"
            v-model="signIn.pass"
            @blur="v$.signIn.pass.$touch"
          />
          <span
            class="sign-in__error"
            v-if="v$.signIn.pass.$error"
          >
            Enter correct password
          </span>
        </div>
        <div class="sign-in__btn-container">
          <button class="sign-in__btn form__btn" :disabled="isSignInBtnDisabled" submit>Sign In</button>
        </div>
        <p>
          Don't have an account?
          <span class="sign-in__link" @click="signUpShow = !signUpShow">Sign Up</span>
        </p>
      </form>
      <!-- ========== /Sign In ========== -->
      <!--===========================================-->
      <div class="sign-in__close close-btn" @click="closeFormSignIn()">
        <img src="../assets/cancel.svg" alt="Close" />
      </div>
    </div>
    <div
      class="sign-in__container fadeIn"
      v-show="signUpShow"
    >
      <h2>Sign up to use our service</h2>
      <!--===========================================-->
      <!-- ========== Sign Up ========== -->
      <form class="sign-in__form" @submit.prevent="submitSignUp">
        <div class="sign-in__input-container">
          <label
            for="fullNameSignUp"
            class="form__label"
            :class="{
              'form__label-error': v$.signUp.fullName.$error,
              'form__label-valid': v$.signUp.fullName.$invalid  === false
            }"
          >
            Full Name
          </label>
          <div class="sign-in__icon_container">
            <div class="sign-in__icon">
              <svg
              class="sign-in__icon"
              width="120"
              height="162"
              viewBox="0 0 120 162"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
              >
              <rect width="120" height="162" fill="white"/>
              <circle :class="{'form__input-error': v$.signUp.fullName.$error, 'form__input-valid': v$.signUp.fullName.$invalid  === false}" cx="62" cy="32" r="25" stroke="black" stroke-width="10"/>
              <path :class="{'form__input-error': v$.signUp.fullName.$error, 'form__input-valid': v$.signUp.fullName.$invalid  === false}" d="M22 105C22 99.7471 23.0346 94.5457 25.0448 89.6927C27.055 84.8396 30.0014 80.4301 33.7157 76.7157C37.4301 73.0014 41.8396 70.055 46.6927 68.0448C51.5457 66.0346 56.7471 65 62 65C67.2529 65 72.4543 66.0346 77.3073 68.0448C82.1604 70.055 86.5699 73.0014 90.2843 76.7157C93.9986 80.4301 96.945 84.8396 98.9552 89.6927C100.965 94.5457 102 99.7471 102 105" stroke="black" stroke-width="10"/>
              <line :class="{'form__input-error': v$.signUp.fullName.$error, 'form__input-valid': v$.signUp.fullName.$invalid  === false}" x1="22" y1="105" x2="22" y2="162" stroke="black" stroke-width="10"/>
              <line :class="{'form__input-error': v$.signUp.fullName.$error, 'form__input-valid': v$.signUp.fullName.$invalid  === false}" x1="102" y1="105" x2="102" y2="162" stroke="black" stroke-width="10"/>
            </svg>
            </div>
          </div>
          <input
            class="sign-in__input form__input"
            :class="{
              'form__input-error': v$.signUp.fullName.$error,
              'form__input-valid': v$.signUp.fullName.$invalid  === false
            }"
            id="fullNameSignUp"
            name="fullName"
            type="text"
            autocomplete="on"
            v-model="signUp.fullName"
            @blur="v$.signUp.fullName.$touch"
          />
          <span
            class="sign-in__error"
            v-if="v$.signUp.fullName.$error"
          >
            Enter correct Full name
          </span>
        </div>
        <div class="sign-in__input-container">
          <label
            for="emailSignUp"
            class="form__label"
            :class="{
              'form__label-error': v$.signUp.email.$error,
              'form__label-valid': v$.signUp.email.$invalid  === false
            }"
          >
            E-mail
          </label>
          <div class="sign-in__icon_container">
            <div class="sign-in__icon">
              <svg
              class="sign-in__icon"
              width="120"
              height="162"
              viewBox="0 0 120 162"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
              >
                <rect width="120" height="162" fill="white"/>
                <rect :class="{'form__input-error': v$.signUp.email.$error, 'form__input-valid': v$.signUp.email.$invalid  === false}" x="5" y="40" width="110" height="82" rx="5" stroke="black" stroke-width="10"/>
                <line :class="{'form__input-error': v$.signUp.email.$error, 'form__input-valid': v$.signUp.email.$invalid  === false}" x1="13.0058" y1="43.0413" x2="59.0413" y2="77.9942" stroke="black" stroke-width="10" stroke-linecap="round"/>
                <line :class="{'form__input-error': v$.signUp.email.$error, 'form__input-valid': v$.signUp.email.$invalid  === false}" x1="60.9587" y1="77.9942" x2="106.994" y2="43.0413" stroke="black" stroke-width="10" stroke-linecap="round"/>
              </svg>
            </div>
          </div>
          <input
            class="sign-in__input form__input"
            :class="{ 'form__input-error': v$.signUp.email.$error, 'form__input-valid': v$.signUp.email.$invalid  === false }"
            id="emailSignUp"
            name="email"
            type="email"
            autocomplete="on"
            v-model="signUp.email"
            @blur="v$.signUp.email.$touch"
          />
          <span
            class="sign-in__error"
            v-if="v$.signUp.email.$error"
          >
            Enter correct email
          </span>
        </div>
        <div class="sign-in__input-container">
          <label
          for="passSignUp"
          class="form__label"
          :class="{
            'form__label-error': v$.signUp.pass.$error,
            'form__label-valid': v$.signUp.pass.$invalid  === false
          }"
          > Password </label>
          <div class="sign-in__icon_container">
            <div class="sign-in__icon">
              <svg
              class="sign-in__icon"
              width="120"
              height="162"
              viewBox="0 0 120 162"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
              >
                <rect width="120" height="162" fill="white"/>
                <rect :class="{'form__input-error': v$.signUp.pass.$error, 'form__input-valid': v$.signUp.pass.$invalid  === false}" x="5" y="67" width="110" height="90" rx="5" stroke="black" stroke-width="10"/>
                <path :class="{'form__input-error': v$.signUp.pass.$error, 'form__input-valid': v$.signUp.pass.$invalid  === false}" d="M20 45C20 39.7626 21.0544 34.5737 23.1058 29.7288C25.1574 24.8836 28.1674 20.4739 31.9696 16.7544C35.7719 13.0346 40.292 10.0783 45.2743 8.05944C50.2568 6.04047 55.6007 5 61 5C66.3993 5 71.7432 6.04047 76.7257 8.05943C81.708 10.0783 86.2281 13.0346 90.0304 16.7544C93.8326 20.4739 96.8426 24.8836 98.8942 29.7288C100.946 34.5737 102 39.7626 102 45" stroke="black" stroke-width="10"/>
                <line :class="{'form__input-error': v$.signUp.pass.$error, 'form__input-valid': v$.signUp.pass.$invalid  === false}" x1="20" y1="45" x2="20" y2="62" stroke="black" stroke-width="10"/>
                <line :class="{'form__input-error': v$.signUp.pass.$error, 'form__input-valid': v$.signUp.pass.$invalid  === false}" x1="102" y1="45" x2="102" y2="62" stroke="black" stroke-width="10"/>
                <circle :class="{'form__input-error-icon': v$.signUp.pass.$error, 'form__input-valid-icon': v$.signUp.pass.$invalid  === false}" cx="30" cy="112" r="10" fill="#010101"/>
                <circle :class="{'form__input-error-icon': v$.signUp.pass.$error, 'form__input-valid-icon': v$.signUp.pass.$invalid  === false}" cx="60" cy="112" r="10" fill="#010101"/>
                <circle :class="{'form__input-error-icon': v$.signUp.pass.$error, 'form__input-valid-icon': v$.signUp.pass.$invalid  === false}" cx="90" cy="112" r="10" fill="#010101"/>
              </svg>
            </div>
          </div>
          <input
            class="sign-in__input form__input"
            :class="{
              'form__input-error': v$.signUp.pass.$error,
              'form__input-valid': v$.signUp.pass.$invalid  === false
            }"
            id="passSignUp"
            name="pass"
            type="password"
            autocomplete="on"
            v-model="signUp.pass"
            @blur="v$.signUp.pass.$touch"
          />
          <span
            class="sign-in__error"
            v-if="v$.signUp.pass.$error"
          >
            Enter correct password
          </span>
        </div>
        <div class="sign-in__input-container">
          <label
          for="passConfirmSignUp"
          class="form__label"
          :class="{
            'form__label-error': v$.signUp.passConfirm.$error,
            'form__label-valid': v$.signUp.passConfirm.$invalid  === false
          }"
          >
            Password confirm
          </label>
          <div class="sign-in__icon_container">
            <div class="sign-in__icon">
              <svg
              class="sign-in__icon"
              width="120"
              height="162"
              viewBox="0 0 120 162"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
              >
                <rect width="120" height="162" fill="white"/>
                <rect :class="{'form__input-error': v$.signUp.passConfirm.$error, 'form__input-valid': v$.signUp.passConfirm.$invalid  === false}" x="5" y="67" width="110" height="90" rx="5" stroke="black" stroke-width="10"/>
                <path :class="{'form__input-error': v$.signUp.passConfirm.$error, 'form__input-valid': v$.signUp.passConfirm.$invalid  === false}" d="M20 45C20 39.7626 21.0544 34.5737 23.1058 29.7288C25.1574 24.8836 28.1674 20.4739 31.9696 16.7544C35.7719 13.0346 40.292 10.0783 45.2743 8.05944C50.2568 6.04047 55.6007 5 61 5C66.3993 5 71.7432 6.04047 76.7257 8.05943C81.708 10.0783 86.2281 13.0346 90.0304 16.7544C93.8326 20.4739 96.8426 24.8836 98.8942 29.7288C100.946 34.5737 102 39.7626 102 45" stroke="black" stroke-width="10"/>
                <line :class="{'form__input-error': v$.signUp.passConfirm.$error, 'form__input-valid': v$.signUp.passConfirm.$invalid  === false}" x1="20" y1="45" x2="20" y2="62" stroke="black" stroke-width="10"/>
                <line :class="{'form__input-error': v$.signUp.passConfirm.$error, 'form__input-valid': v$.signUp.passConfirm.$invalid  === false}" x1="102" y1="45" x2="102" y2="62" stroke="black" stroke-width="10"/>
                <line :class="{'form__input-error': v$.signUp.passConfirm.$error, 'form__input-valid': v$.signUp.passConfirm.$invalid  === false}" x1="49.6989" y1="108.264" x2="57.9414" y2="124.92" stroke="black" stroke-width="10" stroke-linecap="round"/>
                <line :class="{'form__input-error': v$.signUp.passConfirm.$error, 'form__input-valid': v$.signUp.passConfirm.$invalid  === false}" x1="58.1111" y1="125.186" x2="75.2564" y2="94.8889" stroke="black" stroke-width="10" stroke-linecap="round"/>
              </svg>
            </div>
          </div>
          <input
            class="sign-in__input form__input"
            :class="{
              'form__input-error': v$.signUp.passConfirm.$error,
              'form__input-valid': v$.signUp.passConfirm.$invalid  === false
            }"
            id="passConfirmSignUp"
            name="passConfirm"
            type="password"
            autocomplete="on"
            v-model="signUp.passConfirm"
            @blur="v$.signUp.passConfirm.$touch"
          />
          <span
            class="sign-in__error"
            v-if="v$.signUp.passConfirm.$error"
          >
            Enter same password
          </span>
        </div>
        <div class="sign-in__btn-container">
          <button class="sign-in__btn sign-up__btn form__btn" :disabled="isSignUpBtnDisabled" submit>Sign Up</button>
        </div>
      </form>
      <!-- ========== /Sign Up ========== -->
      <!--===========================================-->
      <div class="close-btn sign-in__prev" @click="this.signUpShow = !this.signUpShow">
        <img src="../assets/prev.svg" alt="Prev">
      </div>
      <div class="sign-in__close close-btn" @click="closeFormSignIn()">
        <img src="../assets/cancel.svg" alt="Close" />
      </div>
    </div>
  </div>
</template>

<script>
import useVuelidate from '@vuelidate/core'
import { required, email, minLength, alpha, sameAs } from '@vuelidate/validators'

export default {
  name: 'SignIn',
  props: {
    signInIsOpen: {
      type: Boolean,
      default () {
        return false
      }
    }
  },
  data () {
    return {
      v$: useVuelidate(),
      signUpShow: false,
      signIn: {
        email: '',
        pass: ''
      },
      signUp: {
        fullName: '',
        email: '',
        pass: '',
        passConfirm: ''
      }
    }
  },
  validations () {
    return {
      signIn: {
        email: { required, email },
        pass: { required, minLength: minLength(8) }
      },
      signUp: {
        fullName: { required, alpha, minLength: minLength(1) },
        email: { required, email },
        pass: { required, minLength: minLength(8) },
        passConfirm: { required, sameAs: sameAs(this.signUp.pass) }
      }
    }
  },
  methods: {
    closeFormSignIn () {
      this.$emit('closeFormSignIn')
    },
    submitSignIn () {
      if (this.v$.signIn.email.$invalid || this.v$.signIn.pass.$invalid) {
        console.log('Error')
      } else {
        console.log('No errors')
      }
    },
    submitSignUp () {
      if (this.v$.signUp.fullName.$invalid || this.v$.signUp.email.$invalid || this.v$.signUp.pass.$invalid || this.v$.signUp.passConfirm.$invalid) {
        console.log('Error')
      } else {
        console.log('No errors')
      }
    }
  },
  computed: {
    isSignInBtnDisabled () {
      if (this.v$.signIn.email.$invalid || this.v$.signIn.pass.$invalid) {
        return true
      } else {
        return false
      }
    },
    isSignUpBtnDisabled () {
      if (this.v$.signUp.fullName.$invalid || this.v$.signUp.email.$invalid || this.v$.signUp.pass.$invalid || this.v$.signUp.passConfirm.$invalid) {
        return true
      } else {
        return false
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
@mixin center($horizontal: true, $vertical: true) {
  position: absolute;
  @if ($horizontal and $vertical) {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  } @else if ($horizontal) {
    left: 50%;
    transform: translate(-50%, 0);
  } @else if ($vertical) {
    top: 50%;
    transform: translate(0, -50%);
  }
}

.sign-in {
  &__wrapper {
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.6);
    transition: 1s ease all;
  }
  &__container {
    @include center;
    padding: 70px;
    background-color: #fff;
    border-radius: 20px;
    text-align: center;
  }
  &__input {
    height: 25px;
    &-container {
      position: relative;
      display: flex;
      flex-direction: column;
      text-align: center;
      margin-top: 35px;
    }
  }
  &__icon{
    height: 20px;
    width: auto;
    &_container{
      position: absolute;
      top: 28px;
      left: 9px;
    }
  }
  &__error{
    position: absolute;
    width: 100%;
    left:50%;
    bottom: -16px;
    transform:translateX(-50%);
    font-size: 12px;
    color: rgb(255, 1, 1);
    transition: 0.35s ease-in-out all;
  }
  &__btn {
    margin-top: 50px;
    margin-bottom: 20px;
    width: 100%;
    &-container {
      display: flex;
      justify-content: center;
    }
  }
  &__prev{
    left: 20px;
  }
  &__link {
    text-decoration: underline;
    cursor: pointer;
  }
}
.sign-up__btn{
  margin-top: 50px;
  margin-bottom: 0;
}
.form__label{
  transition: 0.35s ease-in-out all;
  &-error{
    color: red;
  }
  &-valid{
    color: green;
  }
}
.form__input {
  padding: 5px;
  padding-left: 30px;
  border: 1px solid rgb(0, 0, 0);
  border-radius: 10px;
  outline: none;
  transition: 0.35s ease-in-out all;
  &:focus {
    border: 1px solid #005ce6;
  }
  &-error{
    border-color: red;
    stroke: red;
    transition: 0.35s ease-in-out all;
    &-icon{
      stroke: red;
      fill: red;
      transition: 0.35s ease-in-out all;
    }
    &:focus {
      border-color: red;
    }
  }
  &-valid {
    border-color: green;
    stroke: green;
    transition: 0.35s ease-in-out all;
    &-icon{
      stroke: green;
      fill: green;
      transition: 0.35s ease-in-out all;
    }
    &:focus {
      border-color: green;
    }
  }
}

.form__btn {
  padding: 10px;
  color: #fff;
  background-color: #005ce6;
  transition: 0.35s ease-in-out all;
  border-radius: 10px;
  outline: none;
  border: none;
  &:hover {
    cursor: pointer;
    background-color: darken(#005ce6, 10%);
    cursor: default;
  }
  &:disabled {
    background-color: #edeff0;
    color: #a6a6a6;
  }
}

.close-btn {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 20px;
  height: 20px;
  cursor: pointer;
}

.fade-enter-from,
.fade-leave-to {
  transform: scale(0.8);
  opacity: 0;
}
.fade-enter-active,
.fade-leave-active {
  border-radius: 5%;
  transition: 1s ease all;
}
.fade-enter-to {
  transform: scale(1.1);
  opacity: 1;
}

.fadeIn {
  animation-name: fadeIn;
  animation-duration: 1s;
  animation-fill-mode: both;
}
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>

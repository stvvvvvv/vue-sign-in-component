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
  border: 1px solid #adb5bd;
  border-radius: 10px;
  outline: none;
  transition: 0.35s ease-in-out all;
  &:focus {
    border: 1px solid #005ce6;
  }
  &-error{
    border-color: red;
    &:focus {
      border-color: red;
    }
  }
  &-valid {
    border-color: green;
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

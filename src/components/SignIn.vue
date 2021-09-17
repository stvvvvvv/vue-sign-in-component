<template>
  <div class="sign-in__wrapper">
    <div class="sign-in__container">
      <h2>Sign into your account</h2>
      <form class="sign-in__form" action="#" >
        <div class="sign-in__input-container">
          <label for="emailSignIn">
            E-mail
          </label>
          <input
            class="sign-in__input form__input"
            id="emailSignIn"
            name="email"
            type="text"
          />
        </div>
        <div class="sign-in__input-container">
          <label for="passSignIn">
            Password
          </label>
          <input
            class="sign-in__input form__input"
            id="passSignIn"
            name="pass"
            type="password"
          />
        </div>
        <div class="sign-in__btn-container">
          <button class="sign-in__btn form__btn">
            Sign In
          </button>
        </div>
        <p>Don't have an account? <a href="#">Sign Up</a></p>
      </form>
      <div class="sign-in__close close-btn" @click="closeForm()">
        <img src="../assets/cancel.svg" alt="Close">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SignIn',
  methods: {
    closeForm () {
      this.$emit('closeForm')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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

.sign-in{
  &__wrapper{
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.6);
  }
  &__container{
    @include center;
    padding: 70px;
    background-color: #fff;
    border-radius: 20px;
  }
  &__input{
    height: 25px;
    &-container{
      display: flex;
      flex-direction: column;
      text-align: center;
      margin-top: 20px;
    }
  }
  &__btn{
    margin: 20px 0;
    width: 100%;
    &-container{
      display: flex;
      justify-content: center;
    }
  }
}

.form__input{
  padding: 5px;
  border: 1px solid #adb5bd;
  border-radius: 10px;
  outline: none;
  &:focus{
    border: 1px solid #005ce6;
  }
}

.form__btn{
  padding: 10px;
  color: #fff;
  background-color: #005ce6;
  border-radius: 10px;
  outline: none;
  border: none;
  &:hover{
    cursor: pointer;
    background-color: darken(#005ce6, 10%)
  }
}

.close-btn{
  position: absolute;
  top: 20px;
  right: 20px;
  width: 20px;
  height: 20px;
  cursor: pointer;
}
</style>

<template>
  <div class="app">
    <transition name="fade">
      <SignIn @closeFormSignIn="closeFormSignIn" :signInIsOpen="signInIsOpen" class="sign-in" v-if="signInIsOpen"/>
    </transition>
    <nav class="nav">
    <div><a href="#">Home</a></div>
    <div><a href="#">About</a></div>
    <div><a href="#" @click="signInIsOpen = !signInIsOpen">Sign In</a></div>
  </nav>
  <div class="section section-1"></div>
  <div class="section section-2"></div>
  </div>
</template>

<script>
import SignIn from './components/SignIn.vue'

export default {
  name: 'App',
  components: {
    SignIn
  },
  data () {
    return {
      signInIsOpen: false
    }
  },
  methods: {
    closeFormSignIn () {
      this.signInIsOpen = false
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900&display=swap');
$font-color: #010101;
*{
  margin: 0;
  font-family: 'Inter', sans-serif;
  color: $font-color;
  font-size: 16px;
}
.nav{
  display: flex;
  align-items: center;
  height: 50px;
  background-color: #e9c46a;
  div{
    margin-right: 10px;
    &:hover{
      cursor: pointer;
    }
  }
}
.section{
  width: 100%;
  height: 100vh;
  &-1{
    background-color: #264653;
  }
  &-2{
    background-color: #2a9d8f;
  }
}
</style>

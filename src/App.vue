<template>
  <nav class="nav"><SignIn class="sign-in"/></nav>
  <div class="section section-1"></div>
  <div class="section section-2"></div>
</template>

<script>
import SignIn from './components/SignIn.vue'

export default {
  name: 'App',
  components: {
    SignIn
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900&display=swap');
$font-color: #fdfdfd;
*{
  margin: 0;
  font-family: 'Inter', sans-serif;
  color: $font-color;
}
.nav{
  display: flex;
  justify-content: flex-end;
  align-items: center;
  height: 50px;
  background-color: #e9c46a;
}
.sign-in{
  margin-right: 10px;
  cursor: pointer;
  transition: all ease-in-out 0.3s;
  &:hover{
    color:  darken($font-color,70%);
    transition: all ease-in-out 0.3s;
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

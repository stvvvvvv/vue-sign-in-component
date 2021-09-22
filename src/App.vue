<template>
  <router-view />
</template>

<style lang="scss">
.view-fade-enter-from,
.view-fade-leave-to {
  transform: translateX(-1000px);
  transition: 1s ease all;
  opacity: 0;
}
.view-name-enter-active,
.view-fade-leave-active {
  border-radius: 5%;
  transition: 1s ease all;
}
.view-fade-enter-to {
  transform: translateX(0);
  transition: 1s ease all;
  opacity: 1;
}
</style>

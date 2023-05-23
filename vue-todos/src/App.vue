<script setup>
import { RouterLink, RouterView } from 'vue-router'
import TodoHeader from './components/TodoHeader.vue';
</script>

<template>
  <TodoHeader />
  <RouterView />
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300&display=swap" rel="stylesheet');
* {
  font-family: "Poppins", sans-serif;
  margin:0;
  padding:0;
  box-sizing: border-box;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}
</style>


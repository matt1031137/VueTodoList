<script setup>
import { RouterView } from 'vue-router'
import TodoHeader from "./components/TodoHeader.vue"
</script>

<template>
  <TodoHeader />
  <RouterView />
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Clicker+Script&family=Itim&family=Poppins:wght@100;200;300;400;500;600;700;800&family=Roboto+Condensed:ital,wght@0,100..900;1,100..900&family=Rubik:ital,wght@0,300..900;1,300..900&family=Zen+Kurenaido&display=swap');

* {
  font-family: "Rubik", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}
</style>
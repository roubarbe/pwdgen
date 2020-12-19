<template>
  <Home></Home>
</template>

<script>
import Home from './components/Home.vue'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style>


:root{
  --main-color: #3b3b3b;
  --back-color: #d6d6d6;
}

html, body {
  background: var(--back-color);
  color: var(--main-color);
}
#app {
  /* font-family: Helvetica, "Segoe UI", Arial, sans-serif; */
  /* font-size: 12pt; */
}
</style>

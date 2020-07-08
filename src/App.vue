<template>
  <div id="app">
    <app-calculator />
  </div>
</template>

<script>
import AppCalculator from './components/AppCalculator.vue'

export default {
  name: 'App',
  components: {
    AppCalculator
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Karla:wght@400;700&display=swap');

body {
  background: #0a192f;
  color: #333;
  font-family: karla, sans-serif;
}
</style>

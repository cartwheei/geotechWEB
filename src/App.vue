<template>
<div class="alper">
<is-plani-saha-son/>
</div>
</template>

<script>

import isPlaniSahaSon from './components/saha/isPlaniSahaSon'

export default {
   name: 'App',
   components: {
  'is-plani-saha-son':isPlaniSahaSon
      }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

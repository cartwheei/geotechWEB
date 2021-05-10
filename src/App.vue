<template>
<div class="alper">
    <button class="btn btn-dark" v-on:click="comp='tablo'">tablo </button>
  <button class="btn btn-dark" v-on:click="comp='harita'">harita</button>
  <component id="comp" v-bind:is="comp">
  </component>



</div>
</template>

<script>
import tablo from './tabloGenel'
import map from './mapGenel'
export default {
   name: 'App',
   components: {
  'tablo':tablo,
  'harita':map,
      },
      data(){
        return{
          comp:"map"
        }
      },
      methods:{

      }
}
</script>

<style>
#alper {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#comp{
  margin-bottom: 200px;
}
</style>

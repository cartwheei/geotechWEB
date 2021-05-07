<template>
<div class="alper">
  <component v-bind:is="comp"></component>
  <button class="btn btn-dark" v-on:click="comp='is-plani-ofis'">Ofis Tablosu</button>
  <button class="btn btn-dark" v-on:click="comp='is-plani-saha'">Saha Tablosu</button>


</div>
</template>

<script>
import helloWorld from './components/HelloWorld'
import isPlaniSaha from './components/saha/isPlaniSaha'
import isPlaniOfis from './components/ofis/isPlaniOfis'
export default {
   name: 'App',
   components: {
  'is-plani-saha':isPlaniSaha,
  'is-plani-ofis':isPlaniOfis,
  'hello':helloWorld
      },
      data(){
        return{
          comp:"is-plani-saha"
        }
      },
      methods:{

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

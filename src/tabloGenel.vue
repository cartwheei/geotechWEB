<template>
<div class="alper">
    <div class="degisken">
        
        <button class="btn btn-dark" v-on:click="comp='is-plani-ofis'">Ofis Tablosu</button>
        <button class="btn btn-dark" v-on:click="comp='is-plani-saha'">Saha Tablosu</button>
    </div>

  <component v-bind:is="comp"></component>

  </div>

</template>

<script>
import isPlaniSaha from './components/saha/isPlaniSaha'
import isPlaniOfis from './components/ofis/isPlaniOfis'

export default {
   components: {
  'is-plani-saha':isPlaniSaha,
  'is-plani-ofis':isPlaniOfis,
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


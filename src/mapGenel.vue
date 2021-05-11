<template>
  <div class="harita">
    <div id="map"/>
  </div>
  
</template>

<script>
import mapboxgl from "mapbox-gl";
import "mapbox-gl/dist/mapbox-gl.css";
import { onMounted } from "vue";
import axios from 'axios'

export default {
  data(){
    return{
      // iller:[],
      params:{"il_kodlari":[1,2]}
    }
  },
  setup() {
    onMounted(() => {
      console.log(this.iller,'alper')
      mapboxgl.accessToken =
        "pk.eyJ1IjoiY2FydHdoZWVsIiwiYSI6ImNranp4em5rczBjN2Qyb2syOHR2eWhhcGkifQ.JVVl04Dnmq0xIKJiER_C8A   ";
      var map = new mapboxgl.Map({
        container: "map",
        style: "mapbox://styles/mapbox/light-v9",
      });
      map.on('load', () => {
        map.addSource('iller2',{
          'type':'geojson',
          'data':this.iller[0]
        })

        map.addLayer({
          'id': 'maine',
          'type': 'fill',
          'source': 'iller2', // reference the data source
          'layout': {},
          'paint': {
          'fill-color': '#0080ff', // blue color fill
          'fill-opacity': 0.5
          }
          });


      // TODO: Here we want to load a layer
      // TODO: Here we want to load/setup the popup
      });
    });
    return {};
  },
  created(){
          axios.post("http://localhost:2022/geo",this.params).then(response=>{
        
        var iller = response.data.result.features
        // this.iller = response.data.result.features
        console.log(iller,'alper2')
        }).catch(e=>{
          console.log(e)
        })         
  }

  

};
</script>

<style>
#map { position: absolute; top: 100px; bottom: 0; width: 100%; }

</style>
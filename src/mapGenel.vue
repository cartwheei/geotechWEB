<template>
  <div class="harita">
    <div id="map"/>
  </div>
  
</template>

<script>
import mapboxgl from "mapbox-gl";
import "mapbox-gl/dist/mapbox-gl.css";
// import { onMounted } from "vue";
import axios from 'axios'

export default {
  data(){
    return{
      iller:{},
      params:{"il_kodlari":[26,7,9,16,33,48,54,60,10]}
    }
  },

    mounted(){
      mapboxgl.accessToken =
        "pk.eyJ1IjoiY2FydHdoZWVsIiwiYSI6ImNranp4em5rczBjN2Qyb2syOHR2eWhhcGkifQ.JVVl04Dnmq0xIKJiER_C8A   ";
      var map = new mapboxgl.Map({
        container: "map",
        style: "mapbox://styles/mapbox/light-v9",
        zoom:5,
        center:[33.441933,39.487294]
      });
      

      map.on('load', () => {
        map.addSource('iller2',{
          'type':'geojson',
          'data':this.iller
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
    },
    
  
  created(){
    
        axios.post("http://localhost:2022/geo",this.params).then(response=>{
        
        // var iller = response.data.result.features
        this.iller = response.data.result
        console.log(this.iller)
        }).catch(e=>{
          console.log(e)
        })         
  }

  

};
</script>

<style>
#map { position: absolute; top: 100px; bottom: 0; width: 100%; }

</style>
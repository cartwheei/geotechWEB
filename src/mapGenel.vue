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

      // TODO: Here we want to load a layer
      // TODO: Here we want to load/setup the popup

        this.getGeojson(map,this.add_il_layer)

      });
    },
    
  methods:{
      add_il_layer(map,il_geo){
          map.addSource('iller2',{
          'type':'geojson',
          'data':il_geo
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
      },

      getGeojson(map, callback){
        axios.post("http://localhost:2022/geo",this.params).then(response=>{
          console.log(response.data.result)
        callback(map,response.data.result)

        }).catch(e=>{
          console.log(e)
        })  
      }
  },
  created(){
         
  }
  
};
</script>

<style>
#map { position: absolute; top: 100px; bottom: 0; width: 100%; }
</style>
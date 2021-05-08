<template>
    <div id="container">
    <div class="row">
     <h3 class="mt-5">Saha İş Planı Tablosu </h3>
    <div class="col">
    <div class="row">
    <is-plani-tablo-bilgisi/>
    </div>
    <div class="row is-plani-saha">
    <is-plani-saha-verileri v-for="item in todoList"  :key="item.id"  :item="item"/>
    </div>
    </div>
    <div class="row">
    <add-row v-for="item in count" :key="item.id" v-on:addValue="updateTodoList($event)"/>
    </div>
    <div class="row">
    <button v-on:click="veriGetir()" class="btn btn-danger">veri getir</button> 
    <button v-on:click="inputEkle()" class="btn-secondary">Veri Ekle</button>
    </div>
  </div>
</div>


</template>

<script>

import isPlaniSahaVerileri from './isPlaniSahaVerileri'
import addRow from './sahaAddRow'
import axios from 'axios'
import isPlaniTabloBilgisi from './isPlaniTabloBilgisi'
export default {

  components: {
  
  'add-row':addRow,
  'is-plani-tablo-bilgisi':isPlaniTabloBilgisi,
  'is-plani-saha-verileri':isPlaniSahaVerileri
  },
  data(){
    return{
      todoList:[],
      todotext:"",
      veriGiris:false,
      comps:[],
      count:0,
    }
  },
      methods:{
      addTodo(){
        alert('post kısmı')
      },
      veriGetir(){
            axios.get("http://localhost:2022/saha").then(response=>{
          for (let key in response.data.result.features){
            this.todoList.push(response.data.result.features[key].properties)
            console.log(this.todoList)
          }
        }).catch(e=>{
          console.log(e)
        })
      },
      inputEkle(){
        this.comps.push({id:this.count})
        this.count++
      },

      updateTodoList(obj){
        this.todoList.push(obj)
      }
    }
}
</script>
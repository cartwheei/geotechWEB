<template>
    <div id="container">
    <div class="row">
     <h3 class="mt-5">Ofis İş Planı Tablosu</h3>
    <div class="col">
    <div class="row">
    <is-plani-tablo-bilgisi/>
    </div>
    <div class="row is-plani-saha">
    <is-plani-ofis-verileri v-for="item in todoList"  :key="item.id"  :item="item" v-on:rmValue="updateTodoList(undefined,$event)"/>
    </div>
    </div>
    <div class="row">
    <add-row v-for="item in count" :key="item.id" v-on:addValue="updateTodoList($event,undefined)"/>
    </div>
    <div class="row">
    <button v-on:click="veriGetir()" class="btn btn-danger">veri getir</button> 
    <button v-on:click="inputEkle()" class="btn-secondary">Veri Ekle</button>
    </div>
  </div>
</div>


</template>

<script>

import isPlaniOfisVerileri from './isPlaniOfisVerileri'
import addRow from './ofisAddRow'
import axios from 'axios'
import isPlaniTabloBilgisi from './isPlaniTabloBilgisi'
export default {

  components: {
  
  'add-row':addRow,
  'is-plani-tablo-bilgisi':isPlaniTabloBilgisi,
  'is-plani-ofis-verileri':isPlaniOfisVerileri
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
            axios.get("http://localhost:2022/ofis").then(response=>{
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

      updateTodoList(obj1,obj2){
        if(obj1){
        this.todoList.push(obj1)
        }
        if(obj2){
          let index = this.todoList.findIndex(i=>{
            return i.il_kodu == obj2.il_kodu
          })
          this.todoList.splice(index,1)
        }
      }
    }
}
</script>
<template>
    <div class="container">
    
     <h3 class="mt-5">Saha İş Planı Tablosu </h3>
     
    <div class="data--table__container">
    <is-plani-tablo-bilgisi/>
   
    
    <is-plani-saha-verileri v-for="item in todoList"  :key="item.id"  
          :item="item" v-on:rmValueSaha="updateTodoList(undefined,$event)"/>
   
    
    <add-row v-for="item in count" :key="item.id" v-on:addValue="updateTodoList($event,undefined)"/>
    </div>

    <div class="row">
    <button v-on:click="veriGetir()" class="table_button btn btn-danger">veri getir</button> 
    <button v-on:click="inputEkle()" id="input_ekle_saha" class="table_button btn-secondary">Veri Ekle</button>
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
        document.getElementById('input_ekle_saha').style.visibility = 'hidden'
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
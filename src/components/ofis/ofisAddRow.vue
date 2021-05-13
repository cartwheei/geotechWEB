<template>
    <tr>
        
            <td class="col">
                <input id="il_kod" type="text" class="form-control" aria-label="Medium" 
                aria-describedby="inputGroup-sizing-sm" v-model="il_kod">
            </td>
            <td class="col">
                <input id="numarataj" type="text" class="form-control" aria-label="Medium" 
                aria-describedby="inputGroup-sizing-sm" v-model="numarataj">
            </td>
             <td class="col">
                <input id="geometri" type="text" class="form-control" aria-label="Medium" 
                aria-describedby="inputGroup-sizing-sm" v-model="geometri">
            </td>
            <td class="col">
                <input id="toplamIs" type="text" class="form-control" aria-label="Medium"
                 aria-describedby="inputGroup-sizing-sm" v-model="toplamIs">
            </td>
            <td class=" col align-self-medium">
              <button v-on:click="addOfis()" class="btn btn-success">Ekle</button>
            </td>
       
    </tr>
</template>


<script>
import axios from 'axios'

export default {
    props: ['todoList'],

    data(){
        return{
            il_kod:"",
            numarataj:"",
            geometri:"",
            toplamIs:"",
        }
    },
    methods:{
        addOfis(){
            const header={
                'Content-Type': 'application/json;charset=UTF-8',
            }

            var obj = {
                "il_kodu":this.il_kod,
                "numarataj":this.numarataj,
                "geometri":this.geometri,
                "toplam_is":this.toplamIs
            }

            axios.post("http://localhost:2022/ofispost", obj,{
                headers:header}) 
                .then((response)=>{
                console.log(response)
                this.$emit('addValue', obj)
                
            }).catch(error => {
                    if(error.response){
                        console.log(error.response)
                        alert(error.response.data.results.aciklama)
                    }
            })
        }
    }
    
}
</script>
<template>
    <div class="addRow">
        <div class="row">
            <div class="col">
                <input id="il_kod" type="text" class="form-control" aria-label="Medium" 
                aria-describedby="inputGroup-sizing-sm" v-model="il_kod">
            </div>
            <div class="col">
                <input id="personel" type="text" class="form-control" aria-label="Medium" 
                aria-describedby="inputGroup-sizing-sm" v-model="personel">
            </div>
             <div class="col">
                <input id="hamveri" type="text" class="form-control" aria-label="Medium" 
                aria-describedby="inputGroup-sizing-sm" v-model="hamveri">
            </div>
            <div class="col">
                <input id="supurme" type="text" class="form-control" aria-label="Medium" 
                aria-describedby="inputGroup-sizing-sm" v-model="supurme">
            </div>
            <div class="col">
                <input id="toplam" type="text" class="form-control" aria-label="Medium" 
                aria-describedby="inputGroup-sizing-sm" v-model="toplam">
            </div>
            <div class=" col align-self-medium">
              <button v-on:click="addSaha()" class="btn btn-success">Ekle</button>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
        props: ['todoList'],
        data(){
        return{
            il_kod:"",
            personel:"",
            hamveri:"",
            supurme:"",
            toplam:"",
        }
    },
    methods:{
        addSaha(){
            const header={
            'Content-Type': 'application/json;charset=UTF-8',
            }
            
        var obj={
            "il_kodu":this.il_kod,
            "personel_sayı":this.personel,
            "hamveri":this.hamveri,
            "supurme":this.supurme,
            "toplam_is":this.toplam
        }
        console.log(obj)
        axios.post("http://localhost:2022/sahapost", obj,{
                headers:header}) 
                .then((response)=>{
                this.$emit('addValue', obj)
                console.log(response)
            }).catch(error => {
                    if(error.response){
                        console.log(error.response)
                        // alert(error.response.data.results)
                }
            })

        }
    }
}
</script>
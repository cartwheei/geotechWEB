<template>
        <div id="isPlaniSaha">
        <div class="row" >
            <div class="col-8">
                <div class="row">
                <div class="col">
                    <span>{{item.il_kodu}}</span>
                </div>
                <div class="col ">
                    <span>{{item.personel_sayı}}</span>
                </div>
                <div class="col ">
                    <span>{{item.hamveri}}</span>
                </div>
                <div class="col ">
                    <span>{{item.supurme}}</span>
                </div>
                <div class="col ">
                    <span>{{item.toplam_is}}</span>
                </div>
                </div>
            </div>
            <div class=" col align-self-end">
              <button class="btn btn-danger" v-on:click="removeItem()">Sil</button>
              <!-- <button class="btn btn-primary">Güncelle</button> -->
            </div>
        </div>

    </div>
</template>

<script>
import axios from 'axios'

export default {
        props : ["item"],
        data(){
            return{
        }

        },
        methods:{
            removeItem(){

                const header={
                'Content-Type': 'application/json;charset=UTF-8'}
                
                var obj = {"il_kodu":this.item.il_kodu}


                console.log(obj)
                axios.post("http://localhost:2022/sahadel", obj
                ,{'headers':header})
                .then((response)=>{
                this.$emit('rmValueSaha',obj)
                console.log(response)})
                .catch(error => {
                    if(error.response){
                        console.log(error.response,'error response')
                        alert(error.response.data.results)}
            })  
            }
        }
}
</script>
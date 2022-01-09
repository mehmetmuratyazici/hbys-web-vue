<template>
    
    <ul class="list-group">
        <li class="list-group-items justify-content-center d-flex align-items-center mt-2">
            <H2>Tetkik İstek</H2>
        </li>
        <li class="list-group-items justify-content-center d-flex align-items-center mt-2">
            <input type="text" class="form-control" v-model = "infoTetkikIstek.aciklama"  placeholder="Acıklama bilgisini giriniz !">
        </li>
        <li class="list-group-items justify-content-center d-flex align-items-center mt-2">
            <input type="text" class="form-control" v-model="infoTetkikIstek.pol" placeholder="Poliklinik bilgisini giriniz !">
        </li>
        <li class="list-group-items justify-content-center d-flex align-items-center mt-2">
            <input type="text" class="form-control" v-model="infoTetkikIstek.doktor" placeholder="Doktor bilgisini giriniz !">
        </li>
        <li class="list-group-items justify-content-center d-flex align-items-center mt-2">
            <input type="text" class="form-control" v-model="infoTetkikIstek.hasta" placeholder="Hasta bilgisini giriniz !">
        </li>
        <li class="list-group-items justify-content-center d-flex align-items-center mt-2">
            <input type="text" class="form-control" v-model="infoTetkikIstek.tetkik" placeholder="Tetkik bilgisini giriniz !">
        </li>
        <li class="list-group-items justify-content-center d-flex align-items-center mt-2">
            <button @click="save" class="btn btn-success">Kaydet</button>
        </li>
    </ul>   
        <div class="alert alert-success" v-if="showMsg">
           info.message
        </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
            infoTetkikIstek :{
                aciklama:"",
                pol:"",
                doktor:"",
                hasta:"",
                tetkik:"",
            },
            showMsg : false,

                info:{},
        }
    },
    methods: {
        save(){

        axios.post('https://localhost:8098/api/content/tetkikIstek', this.infoTetkikIstek)
                .then(response => (this.info = response))
            
            this.showMsg = true
            setTimeout(() => {
                this.showMsg = false
            }, 3000);
        }
    },
}
</script>
<template>
    
    <ul class="list-group">
        <li class="list-group-items justify-content-center align-items-center d-flex mb-2">
            <h2>Tani Ekle</h2>
        </li>
        <li class="list-group-items justify-content-center align-items-center d-flex mb-2">
            <input type="text" v-model="infoTani.taniAdi" class="form-control" placeholder="Tanı Adını giriniz !">
        </li>
        <li class="list-group-items justify-content-center align-items-center d-flex mb-2">
            <input type="text" v-model="infoTani.taniAciklama" class="form-control" placeholder="Tani açıklamasını giriniz !">
        </li>
        <li class="list-group-items justify-content-center align-items-center d-flex mb-2">
            <input type="text" v-model="infoTani.pol" class="form-control" placeholder="Poliklinik bilgisini giriniz !">
        </li>
        <li class="list-group-items justify-content-center align-items-center d-flex mb-2">
            <input type="text" v-model="infoTani.doktor" class="form-control" placeholder="Doktor bilgisini giriniz !">
        </li>
        <li class="list-group-items justify-content-center align-items-center d-flex mb-2">
            <input type="text" v-model="infoTani.hasta" class="form-control" placeholder="Hasta bilgisini giriniz !">
        </li>
        <li class="list-group-items justify-content-center align-items-center d-flex mb-2">
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
            infoTani :{
                taniAdi:"",
                taniAciklama:"",
                pol:"",
                doktor:"",
                hasta:"",
            },

            showMsg : false,
                info:{},
        }
    },
    methods: {
        save(){
            axios
                .post('https://localhost:8098/api/content/registerTani', this.infoTani)
                .then(response => (this.info = response))
            this.showMsg = true
            setTimeout(() => {
                this.showMsg = false
            }, 3000);
        }
    },
}
</script>
<template>
        <ul class="list-group">
            <li class="mb-2 list-group-items d-flex justify-content-center align-items-center">
                <h3>Hasta Kayıt</h3>
            </li>
            <li class="mb-2 list-group-items d-flex justify-content-center align-items-center">
                <input placeholder="Hata Adı'nı Giriniz !" v-model="infoHasta.adi" class="form-control"/>
            </li>
            <li class="mb-2 list-group-items d-flex justify-content-center align-items-center">
                <input placeholder="Hasta Soyadı'nı Giriniz !" v-model="infoHasta.soyadi" class="form-control"/>
            </li>              
            <li class="mb-2 list-group-items d-flex justify-content-center align-items-center">
                <input placeholder="Hasta Tc Bilgisini Giriniz !" v-model="infoHasta.tc" class="form-control"/>
            </li>              
            <li class="mb-2 list-group-items d-flex justify-content-center align-items-center">
                <input placeholder="Hasta Adres Bilgisini Giriniz !" v-model="infoHasta.adres" class="form-control"/>
            </li>              
            <li class="mb-2 list-group-items d-flex justify-content-center align-items-center">
                <input placeholder="Hasta'nın Geldiği Poliklinik'i Giriniz !" v-model="infoHasta.pol" class="form-control"/>
            </li>              
            <li class="mb-2 list-group-items d-flex justify-content-center align-items-center">
                <input placeholder="Hastanın Doktorunu Giriniz !" v-model="infoHasta.doktor" class="form-control"/>
            </li>        
            <li class="mb-2 list-group-items d-flex justify-content-center align-items-center">
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
            infoHasta : {
                adi:"",
                soyadi:"",
                tc:"",
                adresi:"",
                pol:"",
                doktor:"",
            },

            showMsg : false,
                info:{},
        }
    },
    methods: {
        save(){
            axios
                .post('https://localhost:8098/api/content/registerHasta', this.infoHasta)
                .then(response => (this.info = response))


            
            this.showMsg = true
            setTimeout(() => {
                this.showMsg = false
            }, 3000);
        }
    },
}
</script>
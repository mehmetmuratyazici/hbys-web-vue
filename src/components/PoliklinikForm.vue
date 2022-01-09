<template>
   <ul class="list-group">
       <li class="list-group-items d-flex justify-content-center align-items-center mt-2">
           <h3>Poliklinik Kayıt</h3>
       </li>
       <li class="list-group-items d-flex justify-content-center align-items-center mt-2">
           <input type="text" class="form-control" v-model="infoPol.pol" placeholder="Poliklinik Adını Giriniz !"/>
       </li>
       <li class="list-group-items d-flex justify-content-center align-items-center mt-2">
           <input type="text" class="form-control" v-model="infoPol.doktor" placeholder="Doktor Adını Giriniz !"/>
       </li>
       <li class="list-group-items d-flex justify-content-center align-items-center mt-2">
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
            infoPol:{
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
                .post('https://localhost:8098/api/content/registerPol', this.infoPol)
                .then(response => (this.info = response))
            
            this.showMsg = true
            setTimeout(() => {
                this.showMsg = false
            }, 3000);
        }
    },
}
</script>
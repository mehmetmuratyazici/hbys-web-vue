<template>
    
    <div class="container-flud d-flex bg-primary text-light p-1 mb-2">
        <div class="col">
            <h2>{{title}}</h2>
        </div>
        <div class="col d-flex justify-content-end align-items-center">
            <button @click="selectForm" accesskey="" class="btn btn-primary" :disabled="disabledBtn ==''">Ana Sayfa</button>
            <button @click="selectForm" accesskey="hastaKayit" class="btn btn-primary" :disabled="disabledBtn =='hastaKayit'">Hasta Kayıt</button>
            <button @click="selectForm" accesskey="poliklinikKayit" class="btn btn-primary" :disabled="disabledBtn =='poliklinikKayit'">Poliklinik Kayıt</button>
            <button @click="selectForm" accesskey="taniKayit" class="btn btn-primary" :disabled="disabledBtn =='taniKayit'">Tanı Ekle</button>
            <button @click="selectForm" accesskey="tetkikKayit" class="btn btn-primary" :disabled="disabledBtn =='tetkikKayit'">Tetkik Ekle</button>
        </div>
    </div>
    
</template>

<script>
export default {
    data() {
        return {
            title:"Hbys App",
            disabledBtn:"",
        }
    },
    methods: {
        selectForm(event){
            this.disabledBtn = event.target.accessKey
            //console.log(event.target.accessKey)
            this.$emit("select-Form",event.target.accessKey)
        }
    },
}
</script>


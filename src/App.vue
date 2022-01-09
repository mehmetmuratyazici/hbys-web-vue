<template>
          <div class="container justify-content-center d-flex align-items-center" v-if="splashScreen">
              
              <h2>{{loading}}</h2>
          </div>
          <div class="container-flud" v-else>
              <app-header @select-Form="selectFrom"/>
              <div class="container" v-if="selectedForm == 'hastaKayit'">
                  <HastaForm />

              </div>
              <div class="container" v-else-if="selectedForm == 'poliklinikKayit'">
                  
                  <PoliklinikForm />

              </div>
              <div class="container" v-else-if="selectedForm == 'taniKayit'">
                  
                  <TaniForm/>

              </div>
              <div class="container" v-else-if="selectedForm == 'tetkikKayit'">
                  
                <TetkikIstekForm/>

              </div>
              <div class="justify-content-center d-flex" v-else>
                  
                <h2>Hbys Uygulamasına Hoş Geldiniz ... </h2>

              </div>

          </div>

</template>
    
<script >
import TetkikIstekForm from '@/components/TetkikIstekForm.vue'
import TaniForm from '@/components/TaniForm.vue'
import HastaForm from '@/components/HastaForm.vue'
import PoliklinikForm from '@/components/PoliklinikForm.vue'
export default {
  components : {
      HastaForm,
      PoliklinikForm,
      TaniForm,
      TetkikIstekForm
  },
  data() {
    return {
      showHastaForm: false,
      selectedForm:"",
      splashScreen: true,
      loading:"Loading",
      info: {}
    }
  },
  methods: {
    selectFrom(accessKey){
        console.log(accessKey)

        this.selectedForm = accessKey

    },
  },

  created() {
    var repeat = 0
    var intval = setInterval(() => {
      
      repeat ++

      if(repeat % 4 == 0){
        this.loading = "Loading"

      }
      else
        this.loading += " . "
      
    }, 500);

    setTimeout(() => {
      clearInterval(intval)
        this.splashScreen = false

    },3000)
  }, 
}
</script>
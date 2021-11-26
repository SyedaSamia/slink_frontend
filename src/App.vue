<template>
  <q-layout view="hHh lpR fFf">
    <Header title="SLINK"/>
    <q-page-container>
      <div class="q-py-lg">
        <q-form @submit.prevent="submit(longUrl)">
          <div class="row justify-center">
        <div class="col-6">
            <q-input color="blue" filled type="url" outlined :dense="dense" label="Enter Long Url"/>
          </div>
        </div>
          <div class="q-py-lg">
            <div class="row justify-center">
            <q-btn type="submit" color="primary" label="Get SLINK" />
         </div>
            </div>

        </q-form>

        <Output :shortUrl="shortUrl"/>

      </div>

    </q-page-container>
  </q-layout>
</template>


<script>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Output from './components/Output.vue'
import axios from 'axios'



export default {
  name: 'App',
  components: {
    Header,
    Output,
  },
  data() {
        return {
            output : 'This is your short url....xxxxxxx',
            longUrl : 'https://www.amazon.de/-/en/dp/B08C1KN5J2/ref=gw_de_mz_en_dom_desk_atf1_qc_smp_shp_bf21_p3?pf_rd_r=FCDVYYT4D9QPY77RQ42Z&pf_rd_p=64df09d5-0b67-4616-925c-d85f66593c0f&pd_rd_r=7abd0f48-92b8-4bf9-8cf3-1ad193219bd2&pd_rd_w=5rVjl&pd_rd_wg=iDPkG&ref_=pd_gw_unk',
            shortUrl : ''

        }
    },
     methods: {

       async submit(longUrl) {
         console.log("XYZ " + longUrl)

        try {
          const headers = {

     "Access-Control-Allow-Origin": "*",
     "Access-Control-Allow-Methods" : "POST, GET",
     "Access-Control-Allow-Headers": "Content-Type, Authorization",
//     "Access-Control-Request-Method" : "POST",
  //   "Access-Control-Request-Headers": "Content-Type, Authorization",
     "Content-Type": "application/json",
  };
          const api = "https://slink-urlshortener-backend.herokuapp.com/api/url/shorten/";
       await axios.post(api, {"longUrl": longUrl}, { headers }).then(
          response => {
            this.shortUrl = response.data.shortUrl
            console.log(this.shortUrl)
          }
        )
        }
        catch(error ) {
          console.log("XYZ " + error)
        }

      }

      // onClick () {
      //   this.output = 'Changed output after button click'
      // },

    },



  setup () {
    return {
      leftDrawerOpen: ref(false)
    }
  }
}
</script>


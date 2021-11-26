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
            longUrl : '',
            shortUrl : ''

        }
    },
     methods: {

       async submit(longUrl) {

        try {
          const headers = {
    "Content-Type": "application/json",
     "Access-Control-Allow-Origin": "Origin: http://127.0.0.1:3000",
     "Access-Control-Allow-Methods" : "POST",
     "Access-Control-Allow-Headers": "Content-Type,Authorization"
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
          console.log(error)
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


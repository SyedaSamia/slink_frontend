<template>
  <div class="q-py-lg">
        <q-form @submit.prevent="submit(longUrl)">
          <div class="row justify-center">
            <div class="col-6">
              <q-input color="blue" filled type="url" outlined :dense="dense" label="Enter Long Url" v-model="longUrl"/>
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
</template>

<script>
import Output from './components/Output.vue'
import axios from 'axios'


export default {
  name: 'App',
  components: {
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
          const api = "https://slnk-app.herokuapp.com/api/url/shorten/";
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
}
</script>

<style>

</style>
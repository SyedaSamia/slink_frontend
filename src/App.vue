<template>
  <q-layout view="hHh lpR fFf">
    <Header title="SLINK"/>
    <q-page-container>
      <div class="q-py-lg">
        <q-form @submit.prevent="submit(longUrl)">
          <Input />
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
import Input from './components/Input.vue'
import Output from './components/Output.vue'
import axios from 'axios'



export default {
  name: 'App',
  components: {
    Header,
    Input,
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

       submit: async function(longUrl) {

        try {
          const api = "https://slink-urlshortener-backend.herokuapp.com/api/url/shorten/";
        axios.post(api, {"longUrl": longUrl}).then(
          response => {
            this.shortUrl = response.data.shortUrl
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


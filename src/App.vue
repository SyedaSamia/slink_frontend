<template>
  <q-layout view="hHh lpR fFf">
    <q-space />
    <div class="row justify-center">
      <q-img style="height: 100px; max-width: 100px" alt="Slink logo" src="./assets/slink-logos/slink-logos.jpeg"/>
    </div>
    <q-page-container>
      <div class="q-py-lg">
        <q-form @submit.prevent="submit(longUrl)">

          <div class="q-pa-md doc-container">
            <div class="row justify-center">
              <div class="col">
                <q-input color="brand" filled type="url" outlined :dense="dense" label="Enter Long Url" v-model="longUrl"/>
              </div>
              <div class="col">
                <Button :btnTitle="btnDeleteTitle" :onclick="btnDelete"/>
              </div>
            </div>

          </div>

          <div class="q-py-lg">
            <div class="row justify-center">
                <q-btn type="submit" color="primary" label="Get SLINK" />
            </div>
          </div>
        </q-form>

        <div class="column" v-if="shortUrl != ''">
          <div class="row justify-center">
            <div class="q-pa-md doc-container">
              <div class="row items-start" >
                <Output :shortUrl="shortUrl"/>
              </div>
              <div class="row items-end" >
                <q-icon class="fas fa-copy" @click="copyURL" color="brand"/>
              </div>
            </div>
          </div>

          <div class="q-pa-md flex flex-center">
            <Statistics :statValue="`Total Click: ${shortUrlRedirectedCount}`"/>
            <Statistics :statValue="`Entry: ${longUrlEntryCount}`"/>
          </div>

        </div>


      </div>


    </q-page-container>
  </q-layout>
</template>


<script>
import { ref } from 'vue'
//import Header from './components/Header.vue'
import Output from './components/Output.vue'
import axios from 'axios'
import Button from './components/Button.vue'
import Statistics from './components/Statistics.vue'

export default {
  name: 'App',
  components: {
    //Header,
     Output,
     Button,
     Statistics,
  },

data() {
        return {
            longUrl : '',
            shortUrl : '',
            btnCopyTitle: 'Copy To clipboard',
            btnDeleteTitle: 'Delete',
            longUrlEntryCount: '',
            shortUrlRedirectedCount: '',
            dateCreated: ''


        }
    },
     methods: {

       btnDelete () {
         this.longUrl = ''
         this.shortUrl = ''
       },


       async submit(longUrl) {
         console.log("XYZ " + longUrl)

        try {
          const headers = {

     "Access-Control-Allow-Origin": "*",
     "Access-Control-Allow-Methods" : "POST, GET",
     "Access-Control-Allow-Headers": "Content-Type, Authorization",
     "Content-Type": "application/json",
  };
          const api = "https://s-lnk.herokuapp.com/api/url/shorten/";
       await axios.post(api, {"longUrl": longUrl}, { headers }).then(
          response => {
            this.shortUrl = response.data.shortUrl
            this.longUrlEntryCount = response.data.longUrlEntryCount
            this.shortUrlRedirectedCount = response.data.shortUrlRedirectCount
            this.dateCreated = response.dateCreated
            console.log(this.shortUrl)
          }
        )
        }
        catch(error ) {
          console.log("XYZ " + error)
        }

      },

    async copyURL() {

      if (this.shortUrl != '')
      {
        try {

      await navigator.clipboard.writeText(this.shortUrl);
      alert('Copied');
    } catch($e) {
      alert('Cannot copy');
    }
  }
      },

    },

  setup () {

    return {  leftDrawerOpen: ref(false) }

  }
}
</script>

<style scoped>
.text-brand {
  color: #F6F6F7 !important;
}
.bg-brand {
  background: #F29765 !important;
}

</style>


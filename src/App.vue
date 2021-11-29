<template>
  <q-layout view="hHh lpR fFf">
    <Header title="SLINK"/>
    <q-page-container>
      <div class="q-py-lg">
        <q-form @submit.prevent="submit(longUrl)">
          <div class="row justify-center">
            <div class="col-6">
              <q-input color="blue" filled type="url" outlined :dense="dense" label="Enter Long Url" v-model="longUrl"/>
            </div>
            <Button :btnTitle="btnDeleteTitle" :onclick="btnDelete"/>
          </div>
          <div class="q-py-lg">
            <div class="row justify-center">
                <q-btn type="submit" color="primary" label="Get SLINK" />
            </div>
          </div>

        </q-form>
        <div class="row justify-center" v-if="shortUrl != ''">
          <Output :shortUrl="shortUrl"/>
          <q-icon class="fas fa-copy" @click="copyURL" color="primary"/>


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
import Header from './components/Header.vue'
import Output from './components/Output.vue'
import axios from 'axios'
import Button from './components/Button.vue'
import Statistics from './components/Statistics.vue'



export default {
  name: 'App',
  components: {
    Header,
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
    return {
      leftDrawerOpen: ref(false)
    }
  }
}
</script>


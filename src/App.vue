<template>
  <q-layout view="hHh lpR fFf">
    <Header :title="headerTitle"/>
    <q-separator inset color="#F29765" />
    <q-page-container>
      <div class="q-py-xl">
        <q-form @submit.prevent="submit(longUrl)">
          <div class="row justify-center">
              <div class="col-6">
                <q-input color="brand" filled type="url" outlined :dense="dense" label="Enter Long Url" v-model="longUrl"/>
              </div>
              <Button :btnTitle="`Delete`" :onClick="btnDelete"/>
          </div>

          <div class="q-py-lg">
            <div class="row justify-center">
                <q-btn type="submit" color="brand" label="Get SLINK" />
            </div>
          </div>
        </q-form>

      </div>
        <div class="row justify-center" v-if="urlExist == true">
          <div>
            <v-text-field >
                <div style="color: rgb(102, 65, 65)" class="self-center full-width no-outline">This is a Slink! Please enter a long URL!</div>
           </v-text-field>
          </div>
           <Button :btnTitle="`Restart`" :onClick="btnDelete"/>
        </div>
        <div class="column" v-if="shortUrl != ''&& urlExist == false">

          <div class="q-mb-xl">
            <div class="row justify-center">
            <Output :shortUrl="shortUrl"/>
            <Button :btnTitle="`Copy Link`" :onClick="copyURL"/>
            </div>
          </div>

          <div class="q-py-xl">
             <div class="q-pa-md flex flex-center">
            <Statistics :statValue="`Total Click: ${shortUrlRedirectedCount}`"/>
            <Statistics :statValue="`Entry: ${longUrlEntryCount}`"/>
          </div>

          </div>


        </div>

    </q-page-container >

  </q-layout>
</template>


<script>
import { ref, } from 'vue'
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
            dateCreated: '',
            urlExist: false,
            feedback: '',
            headerTitle: 'Shortened-Link for Boring Long Link!',
            showNullLongUrlMsg: 'Please Enter Long Url!'



        }
    },
     methods: {

       btnDelete () {
         this.longUrl = ''
         this.shortUrl = ''
         this.urlExist = false
       },

       btnFeedback () {
         this.feedbackBtnClick = true
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
       async submit(longUrl) {
         if(longUrl != ''){
           const regex = new RegExp('https?:\\/\\/(www\\.)?s-lnk.herokuapp.com\\/*');
         var res = regex.test(longUrl);

         if(res){
           this.urlExist = true
         }
         else {

           longUrl = longUrl.endsWith('/') ?
        longUrl.slice(0, -1) : longUrl;

        longUrl = longUrl.replace(/^(?:https?:\/\/)?(?:www\.)?/i, "");

        longUrl = "https://" + longUrl;

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
          console.log(error)
        }
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

<style scoped>
.text-brand {
  color: #F6F6F7 !important;
}
.bg-brand {
  background: #F29765 !important;
}

</style>


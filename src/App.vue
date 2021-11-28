<template>
  <q-layout view="hHh lpR fFf">
    <Header title="SLINK"/>
    <q-page-container>
      <Main />

    </q-page-container>
  </q-layout>
</template>


<script>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Main from './components/Main.vue'


export default {
  name: 'App',
  components: {
    Header,
    Main
  },



  setup () {
    return {
      leftDrawerOpen: ref(false)
    }
  }
}
</script>


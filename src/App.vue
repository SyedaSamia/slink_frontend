<template>
  <q-layout view="hHh lpR fFf">
    <Header />
  </q-layout>
</template>


<script>
import { ref } from 'vue'
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header,
  },

  setup () {
    return {
      leftDrawerOpen: ref(false)
    }
  }
}
</script>


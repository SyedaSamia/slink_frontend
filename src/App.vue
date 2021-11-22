<template>
  <q-layout view="hHh lpR fFf">
    <Header />
    <q-page-container>
      <div class="q-py-lg">
        <Input />
        <Button :onClick="onClick"/>

      </div>

    </q-page-container>
  </q-layout>
</template>


<script>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Input from './components/Input.vue'
import Button from './components/Button.vue'

export default {
  name: 'App',
  components: {
    Header,
    Input,
    Button,
  },

  setup () {
    return {
      leftDrawerOpen: ref(false)
    }
  }
}
</script>


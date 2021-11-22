<template>
  <q-layout view="hHh lpR fFf">
    <Header/>
    <q-page-container>
      <div class="q-py-lg">
        <Input />
        <Button :onClick="onClick"/>
        <Output :shortUrl="output"/>

      </div>

    </q-page-container>
  </q-layout>
</template>


<script>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Input from './components/Input.vue'
import Button from './components/Button.vue'
import Output from './components/Output.vue'


export default {
  name: 'App',
  components: {
    Header,
    Input,
    Button,
    Output,
  },
  data() {
        return {
            output : 'This is your short url....xxxxxxx',

        }
    },
     methods: {

      onClick () {
        this.output = 'Changed output after button click'
      }

    },

  setup () {
    return {
      leftDrawerOpen: ref(false)
    }
  }
}
</script>


<template>
  <Header title="SLINK"/>
  <Input />
</template>

<script>
import Header from './components/Header.vue'
import Input from './components/Input/Input.vue'


export default {
  name: 'App',
  components: {
    Header,
    Input,

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
  background: #eee;
}
</style>

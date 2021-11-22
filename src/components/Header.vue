<template>
  <div class="header">
    <h1>{{ title }}</h1>
    <p>
      Get your Shortened Link AKA *SLINK* !
    </p>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    title: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  display: block;
  align-content: center;
  margin-bottom: 30px;
}
</style>

<template>
<div class="q-pa-md">
    <q-toolbar class="bg-white text-brand">

      <q-img style="height: 100px; max-width: 100px" alt="Slink logo" src="../assets/slink-logos/slink-logos.jpeg"/>


      <q-toolbar-title> {{ title }}</q-toolbar-title>


    </q-toolbar>
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

<style>

.text-brand {
  color: #F29765 !important;
}

</style>

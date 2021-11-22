<template>
    <q-header bordered class="bg-primary text-white">
      <q-toolbar>
        <q-toolbar-title>
          {{ title }}
        </q-toolbar-title>
        <q-tooltip>
            fs
        </q-tooltip>
      </q-toolbar>
    </q-header>
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

</style>

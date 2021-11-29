<template>
    <q-header bordered class="bg-primary text-white">
      <div class = 'row'>
        <div class="col">
          <q-avatar>

          </q-avatar>

        </div>
        <div class="col">
          <q-toolbar>
           <q-toolbar-title>
             {{ title }}
            </q-toolbar-title>
           <q-tooltip>
            fs
            </q-tooltip>
          </q-toolbar>
        </div>

      </div>

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

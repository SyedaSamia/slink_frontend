<template>
  <div class="row justify-center">
      <div class="col-6">
           <q-field standout label="Standout" stack-label>
                <template v-slot:control>
                     <div class="self-center full-width no-outline" tabindex="0">{{ shortUrl }}</div>
                  </template>
             </q-field>

      </div>
  </div>
</template>

<script>

export default {
    name: 'Output',
    props: {
        shortUrl: URL

    },


}
</script>

<style>

</style>
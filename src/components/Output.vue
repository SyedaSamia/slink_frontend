<template>
  <div class="row justify-center">
      <div class="col-6">
          <div class="q-py-lg">
              <v-text-field box label="Your shortened Url: " v-model="value">{{ shortUrl }}</v-text-field>
          </div>

      </div>
  </div>
</template>

<script>

export default {
    name: 'Output',
    props: {
        slink: URL,
        shortUrl: URL

    },


}
</script>

<style>

</style>
<template>
  <div class="row justify-center">

      <div class="q-py-md q-pr-md">
           <v-text-field>
                <div style="color: rgb(102, 65, 65)" class="self-center full-width no-outline">Your Slink</div>
           </v-text-field>
      </div>

      <div class="col">
           <q-field color="brand" filled type="url" standout stack-label >
                <div style="color: brand" class="self-center full-width no-outline">{{ shortUrl }}</div>
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
<style scoped>
.text-brand {
  color: #f29965 !important;
}
.bg-brand {
  background: #F29765 !important;
}
</style>
<template>

    <q-circular-progress
      show-value
      class="text-light-blue q-ma-md"
      value="100"
      size="200px"
      color="brand"
      font-size="12px"
    >
    {{ statValue }}
    </q-circular-progress>

</template>

<script>

export default {
    name: 'Statistics',
    props: {
        statValue: String,

    }



}
</script>

<style scoped>
.text-brand {
  color: #F6F6F7 !important;
}
.bg-brand {
  background: #F29765 !important;
}

</style>

<template>

    <q-circular-progress
      show-value
      class="text-rgb(102, 65, 65) q-ma-md"
      value="100"
      size="200px"
      color="brand"
      font-size="15px"
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
  color: #F29765 !important;
}
.bg-brand {
  background: #F29765 !important;
}
</style>
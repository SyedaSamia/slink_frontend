<template>

    <q-circular-progress
      show-value
      class="text-light-orange q-ma-md"
      value="100"
      size="200px"
      color="#F29765"
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

<template>

    <q-circular-progress
      show-value
      class="text-light-blue q-ma-md"
      value="100"
      size="100px"
      color="primary"
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


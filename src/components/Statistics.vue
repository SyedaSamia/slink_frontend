<template>

    <q-circular-progress
      show-value
      class="text-light-blue q-ma-md"
      size="50px"
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


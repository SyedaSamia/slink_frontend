<template>
 <div class="q-pa-md flex flex-center">
    <q-circular-progress
      show-value
      class="text-light-blue q-ma-md"
      size="50px"
      :style="{ color: color}"
    >
    {{ statValue }}
    </q-circular-progress>
 </div>
</template>

<script>

export default {
    name: 'Statistics',
    props: {
        statValue: String,
      color: String
    }



}
</script>


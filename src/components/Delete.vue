<template>
  <q-btn round color="primary" icon="delete" v-model="onCLick"></q-btn>
</template>

<script>

export default {
    name: 'Delete',
    props: {
        onclick: Function

    },


}
</script>

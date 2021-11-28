<template>
  <q-btn round color="primary" icon="copy" v-model="onClick" size="10px"></q-btn>
</template>

<script>

export default {
    name: 'Copy',
    props: {
        onclick: Function

    },


}
</script>

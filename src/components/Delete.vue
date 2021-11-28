<template>
  <q-btn round color="primary" icon="delete" v-model="onClick" size="sm"></q-btn>
</template>

<script>

export default {
    name: 'Delete',
    props: {
        onclick: Function

    },


}
</script>

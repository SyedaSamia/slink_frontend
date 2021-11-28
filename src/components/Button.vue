<template>
  <q-btn flat color="primary" v-model="onClick">{{ btnTitle }}</q-btn>
</template>

<script>

export default {
    name: 'Button',
    props: {
        btnTitle: String,
        onclick: Function

    },


}
</script>

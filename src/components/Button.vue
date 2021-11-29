<template>
  <q-btn flat color="brand" @click="onClick">{{ btnTitle }}</q-btn>
</template>

<script>

export default {
    name: 'Button',
    props: {
        btnTitle: String,
        onClick: Function

    },



}
</script>

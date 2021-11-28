<template>
  <q-btn flat color="primary" @click="onClick">{{ btnTitle }}</q-btn>
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

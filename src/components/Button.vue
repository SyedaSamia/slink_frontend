<template>
  <q-btn flat style="background: white; color: #F29765" @click="onClick">{{ btnTitle }}</q-btn>
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


<template>
  <q-btn flat rounded color="primary" label="{{ btnTitle }}" v-model="onClick"/>
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

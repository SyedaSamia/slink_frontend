<template>
  <q-btn flat style="color: #F29765" @click="onClick" v-bind:title="btnTitle"/>
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
<style scoped>
.text-brand {
  color: #F6F6F7 !important;
}
.bg-brand {
  background: #F29765 !important;
}

</style>

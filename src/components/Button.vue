<template>
    <div class="row justify-center">
        <div class="q-py-lg">
            <q-btn @click="onClick" color="primary" label="Get SLINK" />
        </div>
    </div>
</template>

<script>
export default {
    name: 'Button',
    props: {
        onClick: Function
    }

}
</script>

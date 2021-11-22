<template>
    <div class="row justify-center">
        <div class="col-6">
            <q-input color="blue" filled type="url" outlined :dense="dense" label="Enter Long Url"/>
        </div>
    </div>
</template>

<script>

export default {
    name: 'Input',
    props: {
        label: String,
    }
}
</script>

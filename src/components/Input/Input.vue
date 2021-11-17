<template>
   <label>Enter Your Long Url</label>
   <div>
       <input type="text">
   </div>
   <Button text="Get Slink" color="green"/>
</template>

<script>
import Button from './Button.vue'

export default {
    name: 'Input',
    components: {
        Button,
    },
    data() {
        return {
            
        }
    }

}
</script>

<style scoped>

</style>
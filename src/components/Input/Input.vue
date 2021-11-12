<template>
   <div>
       <label>Enter Your Long Url</label>
       <input class="center-block" required>
       <Button />

   </div>
</template>

<script>
import Button from './Button.vue'

export default {
    name: 'Input',
    components: {
        Button
    }

}
</script>

<style scoped>
div {
    background: white;
    text-align: center;
    border-radius: 10px;
}

.center-block {
    display: block;
    margin-right: auto;
    margin-left: auto;

}

label {
    color: "aaa";
    display: inline-block;


}

input {
    display: block;;
    box-sizing: border-box;
    color: rgb(243, 241, 241);
}

</style>
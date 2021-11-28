<template>
  <li class="list-group-item">
    <a :href="link_url"
         class="text-dark"
         target="_blank"
         rel="noopener noreferrer">{{ link_name }}</a>
    <button @click="copyUrl">copy url from a tag</button>
  </li>
</template>

<script>

export default {
    name: 'Copy',
    props: {
        link_url: URL,
        link_name: String,
        copyUrl: Function


    },


}
</script>

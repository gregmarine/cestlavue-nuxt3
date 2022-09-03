<template>
  <div>
    C'est La Vue - Nuxt 3
  </div>
</template>

<script setup>
useHead({
  script: [
    {
      src: 'https://identity.netlify.com/v1/netlify-identity-widget.js'
    }
  ]
})
</script>
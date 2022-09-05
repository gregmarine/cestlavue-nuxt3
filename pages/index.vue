<template>
  <main>
    C'est La Vue - Nuxt 3
  </main>
</template>

<script setup>
  useHead({
    title: "Welcome to C'est La Vue - Nuxt 3",
    script: [
      {
        src: "https://identity.netlify.com/v1/netlify-identity-widget.js"
      }
    ]
  });
</script>
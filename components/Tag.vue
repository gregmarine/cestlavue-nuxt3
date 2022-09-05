<template>
  <NuxtLink :to="`/tags/${tag}`">
    {{tag}}
  </NuxtLink>
</template>

<script>
  export default {
    props: ['tag']
  }
</script>
<template>
  <NuxtLink :to="`/tags/${props.tag}`">
    {{props.tag}}
  </NuxtLink>
</template>

<script setup>
  const props = defineProps(['tag']);
</script>
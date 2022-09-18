<template>
  <NuxtLink :to="`/tags/${props.tag}`">
    <div class="badge">{{ props.tag }}</div>
  </NuxtLink>
</template>

<script setup>
  const props = defineProps(['tag']);
</script>
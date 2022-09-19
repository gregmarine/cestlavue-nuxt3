<template>
  <span>
    <NuxtLink :to="`/tags/${props.tag}`">
      <div class="badge">{{ props.tag }}</div>
    </NuxtLink>
  </span>
</template>

<script setup>
  const props = defineProps(['tag']);
</script>
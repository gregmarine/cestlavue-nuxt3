<template>
  <Tag v-for="tag of props.tags" :tag="tag" class="mr-2" />
</template>

<script setup>
  const props = defineProps(['tags']);
</script>
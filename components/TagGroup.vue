<template>
  <div>
    <Tag v-for="tag, i of props.tags" :tag="tag" class="mr-2" :key="1"/>
  </div>
</template>

<script setup>
  const props = defineProps(['tags']);
</script>
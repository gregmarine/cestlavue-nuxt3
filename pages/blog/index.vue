<template>
  <div>
    The Blog

    <PostRoll :posts="data" />
  </div>
</template>

<script setup lang="ts">
const { data } = await useAsyncData('posts', () => queryContent('/blog').sort({ date: 1 }).find());
</script>
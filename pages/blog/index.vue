<template>
  <div class="flex flex-col h-screen">
    <Header title="Blog" />

    <div class="container mx-4 md:mx-auto overflow-y-auto pt-8">
      <BlogRoll :posts="data" />
    </div>
  </div>
</template>

<script setup lang="ts">
const { data } = await useAsyncData('posts', () => queryContent('/blog').sort({ date: 1 }).find());
</script>
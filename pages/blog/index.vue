<template>
  <div>
    The Blog

    <PostList :posts="data" />
  </div>
</template>

<script setup lang="ts">
const { data } = await useAsyncData('posts', () => queryContent('/blog').only(['_path', 'title']).find());
</script>
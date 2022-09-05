<template>
  <div>
    The Blog

    <li v-for="post of data" :key="post._path">
      <NuxtLink :to="post._path">{{post.title}}</NuxtLink>
    </li>
  </div>
</template>

<script setup lang="ts">
const { data } = await useAsyncData('posts', () => queryContent('/blog').only(['_path', 'title']).find());
</script>
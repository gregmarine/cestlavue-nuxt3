<template>
  <section>
    <li v-for="post of props.posts" :key="post._path">
      <NuxtLink :to="post._path">{{post.title}}</NuxtLink>
    </li>
  </section>
</template>

<script setup>
  const props = defineProps(['posts']);
</script>
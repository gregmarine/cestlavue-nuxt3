<template>
  <ul class="menu bg-base-100 w-56">
    <li v-for="post of posts" :key="post._path">
      <NuxtLink :to="post._path">
        {{ post.title }}
      </NuxtLink>
    </li>
  </ul>
</template>

<script setup lang="ts">
  const props = defineProps(['path', 'where', 'sort', 'limit']);
  const posts = await queryContent(props.path || {}).where(props.where || {}).sort(props.sort || {}).limit(props.limit).find();
</script>
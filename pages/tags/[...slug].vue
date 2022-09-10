<template>
  <div>
    Posts tagged with #{{ route.params.slug[0] }}
    <PostList :posts="data" />
  </div>
</template>

<script setup lang="ts">
  const route = useRoute();
  const { data } = await useAsyncData('posts', () => queryContent().where({
    tags: { $contains: route.params.slug },
  }).only(['_path', 'title']).find());
</script>
<template>
  <div>
    Posts tagged with {{ route.params.slug[0] }}
    <BlogRoll :posts="posts" />
  </div>
</template>

<script setup lang="ts">
  const route = useRoute();
  const posts = await queryContent().where({
    tags: { $contains: route.params.slug },
  }).sort({ date: 1 }).find();
</script>
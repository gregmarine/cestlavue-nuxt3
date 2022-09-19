<template>
  <div class="flex flex-col h-screen w-screen">
    <Header :title="`Content tagged with ${ route.params.slug[0] }`" />

    <div class="container mx-4 md:mx-auto overflow-y-auto pt-8">
      <ContentRoll :posts="posts" />
    </div>
  </div>
</template>

<script setup lang="ts">
  const route = useRoute();
  const posts = await queryContent().where({
    tags: { $contains: route.params.slug },
  }).sort({ date: 1 }).find();
</script>
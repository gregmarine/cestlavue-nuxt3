<template>
  <div class="flex flex-col h-screen w-screen">
    <Header :title="`Content tagged with ${ route.params.slug[0] }`" />

    <div class="container mx-auto overflow-y-auto pt-8">
      <ContentRoll :where="{ tags: { $contains: route.params.slug }, published: true }" :sort="{ date: -1 }" cta_text="Read More" />
    </div>
  </div>
</template>

<script setup lang="ts">
const route = useRoute();
</script>
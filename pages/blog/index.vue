<template>
  <div class="flex flex-col h-screen w-screen">
    <ContentDoc :path="settings._path" v-slot="{ doc }">
      <Header :title="doc.title" />

      <div class="container mx-auto overflow-y-auto pt-8">
        
        <ContentRenderer :value="doc" class="px-4 md:mx-auto space-y-8 mb-8" />

        <ContentRoll path="blog" :sort="{ date: -1 }" cta_text="Read More" />
      </div>
    </ContentDoc>
  </div>
</template>

<script setup lang="ts">
const settings = await queryContent('/settings/blog').only(['_path', 'title', 'body']).findOne();
</script>
<template>
  <div class="flex flex-col h-screen w-screen">
    <ContentDoc :path="settings._path" v-slot="{ doc }">
      <Header :title="doc.title" />

      <div class="container mx-4 md:mx-auto overflow-y-auto pt-8">
        
        <ContentRenderer :value="doc" class="space-y-8 mb-8" />

        <ContentRoll :posts="posts" />
      </div>
    </ContentDoc>
  </div>
</template>

<script setup lang="ts">
const posts = await queryContent('/blog').sort({ date: 1 }).find();

const settings = await queryContent('/settings/blog').only(['_path', 'title', 'body']).findOne();
</script>
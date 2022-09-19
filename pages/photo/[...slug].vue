<template>
  <div class="flex flex-col h-screen w-screen">
    <ContentDoc v-slot="{ doc }">
      <Header :title="`${ settings.title }: ${ doc.title }`" />

      <div class="container px-4 md:mx-auto h-full max-h-screen overflow-y-auto pt-8 mb-16">
        <ContentRenderer :value="doc" class="space-y-8 mb-8" />
      </div>
    </ContentDoc>
  </div>
</template>

<script setup lang="ts">
const settings = await queryContent('/settings/photo').only(['_path', 'title', 'body']).findOne();
</script>
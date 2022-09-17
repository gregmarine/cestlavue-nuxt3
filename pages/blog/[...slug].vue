<template>
  <div class="flex flex-col h-screen">
    <ContentDoc v-slot="{ doc }">
      <Header :title="`Blog: ${ doc.title }`" />

      <div class="container px-4 md:mx-auto h-full max-h-screen overflow-y-auto pt-8">
        <ContentRenderer :value="doc" class="space-y-8 mb-8" />
      </div>
    </ContentDoc>
  </div>
</template>
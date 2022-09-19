<template>
  <div class="flex flex-col h-screen w-screen">
    <div class="w-screen overflow-y-auto scroll-smooth">
      <div class="hero min-h-screen" :style="`background-image: url(${ settings.hero_image });`">
        <div class="hero-overlay bg-opacity-60"></div>
        <div class="hero-content text-center text-neutral-content">
          <div class="max-w-md">
            <h1 class="mb-5 text-5xl font-bold"><p>{{ settings.title }}</p> <p>{{ settings.sub_title }}</p></h1>
            <p class="mb-5">{{ settings.hero_message }}</p>
            <a href="#content">
              <button class="btn btn-primary">{{ settings.cta_text }}</button>
            </a>
          </div>
        </div>
      </div>

      <div id="content"></div>

      <ContentDoc :path="blogSettings._path" v-slot="{ doc }">
        <div v-if="blogSettings.landing" class="container mx-4 md:mx-auto overflow-y-auto pt-8">
          <NuxtLink to="/blog">
            <button class="btn btn-link">{{ blogSettings.title }}</button>
          </NuxtLink>
          <ContentRoll :posts="blogPosts" />
        </div>
      </ContentDoc>
    </div>
  </div>
</template>

<script setup>
  const settings = await queryContent('/settings/general').findOne();

  const blogSettings = await queryContent('/settings/blog').findOne();
  const blogPosts = await queryContent('/blog').sort({ date: 1 }).limit(3).find();

  useHead({
    title: "Landing Page"
  })
</script>
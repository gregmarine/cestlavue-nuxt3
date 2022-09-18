<template>
  <div>
    <Head>
      <Title>{{ settings.title }}</Title>
      <Script src="https://identity.netlify.com/v1/netlify-identity-widget.js" />
    </Head>
    
    <div class="hero min-h-screen" :style="`background-image: url(${ settings.hero_image });`">
      <div class="hero-overlay bg-opacity-60"></div>
      <div class="hero-content text-center text-neutral-content">
        <div class="max-w-md">
          <h1 class="mb-5 text-5xl font-bold"><p>{{ settings.title }}</p> <p>{{ settings.sub_title }}</p></h1>
          <p class="mb-5">{{ settings.hero_message }}</p>
          <button class="btn btn-primary">{{ settings.cta_text }}</button>
        </div>
      </div>
    </div>

    <ContentDoc :path="blogSettings._path" v-slot="{ doc }">
      <div class="container mx-4 md:mx-auto overflow-y-auto pt-8">
        <NuxtLink to="/blog">
          <button class="btn btn-link">{{ blogSettings.title }}</button>
        </NuxtLink>
        <ContentRoll :posts="blogPosts" />
      </div>
    </ContentDoc>
  </div>
</template>

<script setup>
  const settings = await queryContent('/settings/general').findOne();

  const blogSettings = await queryContent('/settings/blog').only(['_path', 'title', 'body']).findOne();
  const blogPosts = await queryContent('/blog').sort({ date: 1 }).limit(3).find();
</script>
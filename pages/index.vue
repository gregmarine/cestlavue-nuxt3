<template>
  <div class="container flex flex-col h-screen w-screen">
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

      <ContentDoc v-if="blogSettings.landing" :path="blogSettings._path" v-slot="{ doc }">
        <div class="container mx-auto overflow-y-auto pt-8">
          <div class="divider">
            <NuxtLink to="/blog">
              <button class="btn btn-link">{{ blogSettings.title }}</button>
            </NuxtLink>
          </div>
          <ContentRoll :posts="blogPosts" />
        </div>
      </ContentDoc>

      <ContentDoc v-if="artSettings.landing" :path="artSettings._path" v-slot="{ doc }">
        <div class="container mx-auto overflow-y-auto pt-8">
          <div class="divider">
            <NuxtLink to="/art">
              <button class="btn btn-link">{{ artSettings.title }}</button>
            </NuxtLink>
          </div>
          <ContentRoll :posts="artPosts" />
        </div>
      </ContentDoc>

      <ContentDoc v-if="photoSettings.landing" :path="photoSettings._path" v-slot="{ doc }">
        <div class="container mx-auto overflow-y-auto pt-8">
          <div class="divider">
            <NuxtLink to="/photo">
              <button class="btn btn-link">{{ photoSettings.title }}</button>
            </NuxtLink>
          </div>
          <ContentRoll :posts="photoPosts" />
        </div>
      </ContentDoc>
    </div>
  </div>
</template>

<script setup>
  const settings = await queryContent('/settings/general').findOne();

  const blogSettings = await queryContent('/settings/blog').findOne();
  const blogPosts = await queryContent('/blog').sort({ date: 1 }).limit(3).find();

  const artSettings = await queryContent('/settings/art').findOne();
  const artPosts = await queryContent('/art').sort({ date: 1 }).limit(3).find();

  const photoSettings = await queryContent('/settings/photo').findOne();
  const photoPosts = await queryContent('/photo').sort({ date: 1 }).limit(3).find();

  useHead({
    title: "Landing Page",
    meta: [
      {
        name: "description",
        content: settings.hero_message
      },
      {
        property: "site_name",
        content: settings.title
      },
      {
        property: "og:title",
        content: settings.title
      },
      {
        property: "og:description",
        content: settings.hero_message
      },
      {
        property: "og:type",
        content: "article"
      },
      {
        property: "og:url",
        content: settings.base_url
      },
      {
        property: "og:image",
        content: settings.base_url + settings.social_image
      },
      {
        property: "og:image:url",
        content: settings.base_url + settings.social_image
      },
      {
        property: "og:image:secure_url",
        content: settings.base_url + settings.social_image
      },
      {
        property: "og:image:alt",
        content: settings.social_image_alt
      },
      {
        name: "twitter:card",
        content: "summary_large_image"
      },
      {
        name: "twitter:site",
        content: "https://twitter.com/" + settings.twitter
      },
      {
        name: "twitter:site:id",
        content: "https://twitter.com/" + settings.twitter
      },
      {
        name: "twitter:creator",
        content: "https://twitter.com/" + settings.twitter
      },
      {
        name: "twitter:creator:id",
        content: "https://twitter.com/" + settings.twitter
      },
      {
        name: "twitter:title",
        content: settings.title
      },
      {
        name: "twitter:text:title",
        content: settings.title
      },
      {
        name: "twitter:description",
        content: settings.hero_message
      },
      {
        name: "twitter:url",
        content: settings.base_url
      },
      {
        name: "twitter:image:src",
        content: settings.base_url + settings.social_image
      },
      {
        name: "twitter:image",
        content: settings.base_url + settings.social_image
      },
      {
        name: "twitter:image:alt",
        content: settings.social_image_alt
      },
    ]
  })
</script>
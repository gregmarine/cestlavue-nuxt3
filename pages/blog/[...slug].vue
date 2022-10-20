<template>
  <div class="flex flex-col h-screen w-screen">
    <ContentDoc v-slot="{ doc }">
      <Head>
        <Meta name="description" :content="doc.description" />
        <Meta property="site_name" :content="doc.title" />
        <Meta property="og:title" :content="doc.title" />
        <Meta property="og:description" :content="doc.description" />
        <Meta property="og:type" content="article" />
        <Meta property="og:url" :content="`${generalSettings.base_url}${doc._path}`" />
        <Meta property="og:image" :content="`${generalSettings.base_url}${doc.featured_image}`" />
        <Meta property="og:image:url" :content="`${generalSettings.base_url}${doc.featured_image}`" />
        <Meta property="og:image:secure_url" :content="`${generalSettings.base_url}${doc.featured_image}`" />
        <Meta property="og:image:alt" :content="doc.title" />
        <Meta name="twitter:card" content="summary_large_image" />
        <Meta name="twitter:site" :content="`https://twitter.com/${generalSettings.twitter}`" />
        <Meta name="twitter:site:id" :content="`https://twitter.com/${generalSettings.twitter}`" />
        <Meta name="twitter:creator" :content="`https://twitter.com/${generalSettings.twitter}`" />
        <Meta name="twitter:creator:id" :content="`https://twitter.com/${generalSettings.twitter}`" />
        <Meta name="twitter:title" :content="doc.title" />
        <Meta name="twitter:text:title" :content="doc.title" />
        <Meta name="twitter:description" :content="doc.description" />
        <Meta name="twitter:url" :content="`${generalSettings.base_url}${doc._path}`" />
        <Meta name="twitter:image:src" :content="`${generalSettings.base_url}${doc.featured_image}`" />
        <Meta name="twitter:image" :content="`${generalSettings.base_url}${doc.featured_image}`" />
        <Meta name="twitter:image:alt" :content="doc.title" />
      </Head>
      <Header :title="`${ settings.title }: ${ doc.title }`" />

      <div class="px-4 mx-auto h-full max-h-screen overflow-y-auto mb-16 prose dark:prose-invert">
        <ContentRenderer :value="doc" class="space-y-8 mb-8" />
      </div>
    </ContentDoc>
  </div>
</template>

<script setup lang="ts">
const settings = await queryContent('/settings/blog').only(['_path', 'title', 'body']).findOne();
const generalSettings = await queryContent('/settings/general').findOne();
</script>
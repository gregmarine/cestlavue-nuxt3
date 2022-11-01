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

      <div :class="`px-4 ${ !doc.top_level ? 'md:mx-auto lg:mx-48 xl:mx-96' : 'mx-auto' }  h-full max-h-screen overflow-y-auto pt-8 mb-16`">
        <div v-if="!doc.top_level" class="flex justify-center">
          <div class="card w-full lg:w-1/2 shadow-xl mb-8">
            <figure>
              <!-- The clicking the image will open it into a larger modal -->
              <label for="image-modal">
                <img v-if="doc.featured_image" :src="doc.featured_image" :alt="doc.title" />
              </label>
            </figure>
          </div>
        </div>
        <ContentRenderer :value="doc" class="space-y-8 mb-8" />

        <ContentRoll v-if="doc.top_level" :path="doc._path" :where="{ top_level: false, published: true }" :sort="{ date: -1 }" cta_text="Read More" />
      </div>

      <!-- Put this part before </body> tag -->
      <input type="checkbox" id="image-modal" class="modal-toggle" />
      <div class="modal">
        <div class="modal-box w-11/12 max-w-5xl">
          <label for="image-modal" class="btn btn-sm btn-circle absolute right-2 top-2">✕</label>
          <img v-if="doc.featured_image" :src="doc.featured_image" :alt="doc.title" />
        </div>
      </div>
    </ContentDoc>
  </div>
</template>

<script setup lang="ts">
const settings = await queryContent('/settings/gallery').only(['_path', 'title', 'body']).findOne();
const generalSettings = await queryContent('/settings/general').findOne();
</script>
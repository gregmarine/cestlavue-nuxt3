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
        <div v-if="doc.featured_image" class="flex justify-center">
          <div class="card w-full lg:w-1/2 shadow-xl mb-8">
            <figure>
              <img :src="doc.featured_image" :alt="doc.title" />
            </figure>
          </div>
        </div>
        
        <ContentRenderer :value="doc" class="space-y-8 mb-8" />

        <div tabindex="0" class="collapse collapse-arrow border border-base-300 bg-base-100 rounded-box">
          <div class="collapse-title text-xl font-medium">
            Ingredients
          </div>
          <div class="collapse-content"> 
            <ul class="list-none bg-base-100 mb-16">
              <li v-for="ingredient, i of doc.ingredients" :key="i">
                {{ ingredient.qty }} {{ ingredient.unit }} {{ ingredient.ingredient }} <span v-if="ingredient.note !== ''">({{ ingredient.note }})</span>
              </li>
            </ul>
          </div>
        </div>

        <div tabindex="1" class="collapse collapse-arrow border border-base-300 bg-base-100 rounded-box">
          <div class="collapse-title text-xl font-medium">
            Instructions
          </div>
          <div class="collapse-content"> 
            <ol class="list-decimal bg-base-100 mb-16">
              <li v-for="instruction, i of doc.instructions" :key="i">
                {{ instruction.instruction }}
              </li>
            </ol>
          </div>
        </div>

        <div tabindex="2" class="collapse collapse-arrow border border-base-300 bg-base-100 rounded-box">
          <div class="collapse-title text-xl font-medium">
            Notes
          </div>
          <div class="collapse-content"> 
            {{ doc.notes }}
          </div>
        </div>
      </div>
    </ContentDoc>
  </div>
</template>

<script setup lang="ts">
const settings = await queryContent('/settings/recipes').only(['_path', 'title', 'body']).findOne();
const generalSettings = await queryContent('/settings/general').findOne();
</script>
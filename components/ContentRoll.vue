<template>
  <div class="grid justify-items-center sm:grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 gap-8 mb-16">
    <div v-for="post of posts" :key="post._path" class="card w-96 bg-base-100 shadow-xl">
      <figure><img v-if="post.featured_image" :src="post.featured_image" :alt="post.title" /></figure>
      <div class="card-body">
        <h2 class="card-title">{{ post.title }}</h2>
        <p><TagGroup :tags="post.tags"></TagGroup></p>
        <p>{{ post.description }}</p>
        <div class="card-actions justify-end">
          <NuxtLink :to="post._path">
            <button class="btn btn-primary">{{ props.cta_text }}</button>
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
  const props = defineProps(['path', 'where', 'sort', 'limit', 'cta_text']);
  const posts = await queryContent(props.path || {}).where(props.where || {}).sort(props.sort || {}).limit(props.limit).find();
</script>
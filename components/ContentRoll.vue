<template>
  <div class="grid sm:grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 gap-8 mb-16">
    <div v-for="post of props.posts" :key="post._path" class="card w-96 bg-base-100 shadow-xl">
      <figure><img :src="post.featured_image" alt="" /></figure>
      <div class="card-body">
        <h2 class="card-title">{{ post.title }}</h2>
        <p><TagGroup :tags="post.tags"></TagGroup></p>
        <p>{{ post.description }}</p>
        <div class="card-actions justify-end">
          <NuxtLink :to="post._path">
            <button class="btn btn-primary">Read more</button>
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
  const props = defineProps(['posts']);
</script>
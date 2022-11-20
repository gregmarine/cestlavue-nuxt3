<template>
  <ul class="menu menu-horizontal bg-base-100">
    <li v-if="prev">
      <NuxtLink :to="prev._path">
        <img src="/assets/icons/arrow-back-outline.svg" class="w-8" />
        {{ prev.title }}
      </NuxtLink>
    </li>
    <li>
      <NuxtLink :to="toc">
        <img src="/assets/icons/menu-outline.svg" class="w-8" />
      </NuxtLink>
    </li>
    <li v-if="next">
      <NuxtLink :to="next._path">
        {{ next.title }}
        <img src="/assets/icons/arrow-forward-outline.svg" class="w-8" />
      </NuxtLink>
    </li>
  </ul>
</template>

<script setup lang="ts">
  const props = defineProps(['path', 'where', 'sort']);
  const toc = props.path.substring(0, props.path.lastIndexOf('/'));
  const [prev, next] = await queryContent(toc).only(['_path', 'title']).where(props.where || {}).sort(props.sort || {}).findSurround(props.path);
</script>
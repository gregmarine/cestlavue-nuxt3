<template>
  <div class="grid grid-cols-3 gap-4">
    <div>
      <NuxtLink v-if="prev" :to="prev._path" class="inline-flex">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mt-1" fill="none" viewBox="0 0 512 512"><title>ionicons-v5-a</title><polyline points="244 400 100 256 244 112" style="fill:none;stroke:currentColor;stroke-linecap:round;stroke-linejoin:round;stroke-width:48px"/><line x1="120" y1="256" x2="412" y2="256" style="fill:none;stroke:currentColor;stroke-linecap:round;stroke-linejoin:round;stroke-width:48px"/></svg>
        {{ prev.title }}
      </NuxtLink>
    </div>
    <div class="flex justify-center">
      <NuxtLink :to="toc">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 512 512"><title>ionicons-v5-j</title><line x1="80" y1="160" x2="432" y2="160" style="fill:none;stroke:currentColor;stroke-linecap:round;stroke-miterlimit:10;stroke-width:32px"/><line x1="80" y1="256" x2="432" y2="256" style="fill:none;stroke:currentColor;stroke-linecap:round;stroke-miterlimit:10;stroke-width:32px"/><line x1="80" y1="352" x2="432" y2="352" style="fill:none;stroke:currentColor;stroke-linecap:round;stroke-miterlimit:10;stroke-width:32px"/></svg>
      </NuxtLink>
    </div>
    <div class="flex justify-end">
      <NuxtLink v-if="next" :to="next._path" class="inline-flex">
        {{ next.title }}
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mt-1" viewBox="0 0 512 512"><title>ionicons-v5-a</title><polyline points="268 112 412 256 268 400" style="fill:none;stroke:currentColor;stroke-linecap:round;stroke-linejoin:round;stroke-width:48px"/><line x1="392" y1="256" x2="100" y2="256" style="fill:none;stroke:currentColor;stroke-linecap:round;stroke-linejoin:round;stroke-width:48px"/></svg>
      </NuxtLink>
    </div>
  </div>
</template>

<script setup lang="ts">
  const props = defineProps(['path', 'where', 'sort']);
  const toc = props.path.substring(0, props.path.lastIndexOf('/'));
  const [prev, next] = await queryContent(toc).only(['_path', 'title']).where(props.where || {}).sort(props.sort || {}).findSurround(props.path);
</script>
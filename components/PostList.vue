<template>
  <section>
    <li v-for="post of posts" :key="post._path">
      <NuxtLink :to="post._path">{{post.title}}</NuxtLink>
    </li>
  </section>
</template>

<script>
  export default {
    props: ['posts']
  }
</script>
<template>
  <header>
    <Head>
      <Title>{{ props.title }}</Title>
    </Head>
    <div class="navbar bg-base-100 shadow-xl">
      {{ props.title }}
    </div>
  </header>
</template>

<script setup>
  const props = defineProps(['title']);
</script>
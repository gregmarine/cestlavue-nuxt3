<template>
  <div>
    <Head>
      <Title>{{ data.title }}</Title>
      <Script src="https://identity.netlify.com/v1/netlify-identity-widget.js" />
    </Head>
    <Header :title="data.title" />
    C'est La Vue - Nuxt 3
  </div>
</template>

<script setup>
  const { data } = await useAsyncData('settings', () => queryContent('/settings/general').only(['_path', 'title']).findOne());
</script>
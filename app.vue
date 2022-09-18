<template>
  <div>
    <Head>
      <Meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1 maximum-scale=1, viewport-fit=cover, user-scalable=no" />
      <Meta name="format-detection" content="telephone=no" />
      <Meta name="apple-mobile-web-app-capable" content="yes" />
      <Meta name="apple-mobile-web-app-title" :content="settings.title" />
      <Meta name="apple-mobile-web-app-status-bar-style" content="black" />
    </Head>
    <NuxtPage />
  </div>
</template>

<script setup>
  const settings = await queryContent('/settings/general').findOne();
</script>
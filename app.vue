<template>
  <div>
    <NuxtPage />
  </div>
</template>

<script setup>
  const settings = await queryContent('/settings/general').findOne();

  useHead({
    titleTemplate: (title) => {
      return title ? `${ settings.title } - ${ title }` : settings.title
    },
    meta: [
      {
        name: "viewport",
        content: "viewport-fit=cover,width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no"
      },
      {
        name: "format-detection",
        content: "telephone=no"
      },
      {
        name: "msapplication-tap-highlight",
        content: "no"
      },
      {
        name: "apple-mobile-web-app-capable",
        content: "yes"
      },
      {
        name: "apple-mobile-web-app-title",
        content: settings.title
      },
      {
        name: "apple-mobile-web-app-status-bar-style",
        content: "black"
      }
    ],
    script: [
      {
        src: "https://identity.netlify.com/v1/netlify-identity-widget.js"
      }
    ]
  });
</script>
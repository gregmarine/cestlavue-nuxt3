<template>
  <div>
    <Head>
      <Title>{{ data.title }}</Title>
      <Script src="https://identity.netlify.com/v1/netlify-identity-widget.js" />
    </Head>
    
    <div class="hero min-h-screen" :style="`background-image: url(${ data.hero_image });`">
      <div class="hero-overlay bg-opacity-60"></div>
      <div class="hero-content text-center text-neutral-content">
        <div class="max-w-md">
          <h1 class="mb-5 text-5xl font-bold"><p>Greg Marine</p> <p>"The Website"</p></h1>
          <p class="mb-5">On this site, you'll find a collection of my writing, photography, art, and recipes. Thank you for dropping by!</p>
          <button class="btn btn-primary">Get Started</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
  const { data } = await useAsyncData('settings', () => queryContent('/settings/general').only(['title', 'hero_image']).findOne());
</script>
<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>
          C'est La Vue - Nuxt 3
        </ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      <NuxtLink to="/blog">Blog</NuxtLink>
    </ion-content>
  </ion-page>
</template>

<script setup>
  import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from "@ionic/vue";

  useHead({
    title: "Welcome to C'est La Vue - Nuxt 3",
    script: [
      {
        src: "https://identity.netlify.com/v1/netlify-identity-widget.js"
      }
    ]
  });
</script>
<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>
          C'est La Vue - Nuxt 3 - Blog
        </ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      <PostList :posts="data" />
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
  import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from "@ionic/vue";

  const { data } = await useAsyncData('posts', () => queryContent('/blog').only(['_path', 'title']).find());
</script>
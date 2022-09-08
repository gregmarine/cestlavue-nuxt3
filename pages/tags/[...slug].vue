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
      Posts tagged with #{{ route.params.slug[0] }}
      <PostList :posts="data" />
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
  import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from "@ionic/vue";
  
  const route = useRoute();
  const { data } = await useAsyncData('posts', () => queryContent().where({
    tags: { $contains: route.params.slug },
  }).only(['_path', 'title']).find());
</script>
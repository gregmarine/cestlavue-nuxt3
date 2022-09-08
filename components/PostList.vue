<template>
  <ion-list>
    <ion-item v-for="post of props.posts" :key="post._path">
      <NuxtLink :to="post._path">{{post.title}}</NuxtLink>
    </ion-item>
  </ion-list>
</template>

<script setup>
  import { IonList, IonItem } from "@ionic/vue";
  const props = defineProps(['posts']);
</script>
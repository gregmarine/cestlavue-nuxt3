<template>
  <header class="relative">
    <div class="navbar bg-base-100 shadow-xl">
      <div class="navbar-start lg:hidden">
        <div class="dropdown">
          <label tabindex="0" class="btn btn-ghost">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h8m-8 6h16" /></svg>
          </label>
          <ul tabindex="0" class="menu menu-compact dropdown-content mt-3 p-2 shadow bg-base-100 rounded-box w-52">
            <li v-for="collection of collections">
              <NuxtLink :to="`/${ collection.title.toLowerCase() }`">
                {{ collection.title }}
              </NuxtLink>
            </li>
          </ul>
        </div>
      </div>

      <div class="navbar-center lg:navbar-start">
        {{ props.title }}
      </div>

      <div class="navbar-end hidden lg:flex">
        <ul class="menu menu-horizontal p-0">
          <li v-for="collection of collections">
            <NuxtLink :to="`/${ collection.title.toLowerCase() }`">
              {{ collection.title }}
            </NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </header>
</template>

<script setup>
  const props = defineProps(['title']);

  const collections = await queryContent('/settings').where({ menu: true }).find();
</script>
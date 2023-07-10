<template>
  <div>
    <h1 class="heading">index</h1>
    <nuxt-link to="/posts">posts</nuxt-link>
  </div>
</template>

<script setup>
  const { data } = await useAsyncData('data', () => queryContent('/').find());
</script>

<style scoped>
  .heading {
    view-transition-name: heading;
  }
</style>

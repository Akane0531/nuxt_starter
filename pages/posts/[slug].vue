<template>
  <main>
    <!-- <h1>{{ data.title }}</h1> -->
    <!-- <ContentRenderer :value="data" /> -->
    <p>{{ $route.params.slug }}</p>
    <p>{{ $route.path }}</p>
    <ContentQuery :path="$route.path" v-slot="{ data }">
      <ContentRenderer :value="data" />
    </ContentQuery>
    <!-- <pre>{{ data }}</pre> -->
  </main>
</template>

<script setup>
  import { useRoute } from 'vue-router';
  const route = useRoute();
  // const slug = route.params.slug === 'index' ? '' : route.params.slug;
  console.log(route);
  // const { data } = await useAsyncData('data', () => queryContent(`/${slug}`).findOne());
</script>

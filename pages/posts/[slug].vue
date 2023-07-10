<template>
  <main>
    <p>slug: {{ $route.params.slug }}</p>
    <p>path: {{ $route.path }}</p>
    <div v-if="data" :style="transitionNames(data._path)">
      <img v-if="data.thumbnail" class="thumbnail" :src="`../../assets/image/${data.thumbnail}`" alt="" />
      <h1 v-if="data.title" class="title">{{ data.title }}</h1>
      <nuxt-link to="/posts">posts</nuxt-link>
      <ContentRenderer :value="data" />
      <!-- <pre>{{ data }}</pre> -->
    </div>
    <div v-else>
      <h1>お探しのページは見つかりませんでした</h1>
    </div>
  </main>
</template>

<script setup>
  import { useRoute } from 'vue-router';
  const route = useRoute();
  const path = () => route.path.replace(/(.*\/)index/, '$1'); // ファイル名がindex用 そもそもindexにしない方が良い
  const transitionNames = (id) => {
    const prefix = id.replace(/\//g, '-');
    const names = {
      ['--transition-title']: `${prefix}-title`,
      ['--transition-thumbnail']: `${prefix}-thumbnail`
    };

    return names;
  };

  const { data } = await useAsyncData('data', () => queryContent(`${path()}`).findOne());
</script>

<style scoped>
  .view-transition {
    view-transition-name: var(--transition-name);
  }
  .title {
    view-transition-name: var(--transition-title);
  }
  .thumbnail {
    view-transition-name: var(--transition-thumbnail);
    max-width: 100%;
  }
</style>

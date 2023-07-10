<template>
  <div>
    <h1 class="heading">posts/index</h1>
    <ContentList path="/" v-slot="{ list }">
      <div v-for="data in list" :key="data._path" :style="transitionNames(data._path)">
        <nuxt-link :to="data._path" v-if="data.thumbnail">
          <img class="thumbnail" v-if="data.thumbnail" :src="`../../assets/image/${data.thumbnail}`" alt="" />
        </nuxt-link>
        <nuxt-link :to="data._path" v-if="data.title">
          <h2 class="title">{{ data.title }}</h2>
        </nuxt-link>
        <p>{{ data.description }}</p>
        <!-- <pre>{{ data }}</pre> -->
      </div>
    </ContentList>
  </div>
</template>

<script setup>
  const transitionNames = (id) => {
    const prefix = id.replace(/\//g, '-');
    const names = {
      ['--transition-title']: `${prefix}-title`,
      ['--transition-thumbnail']: `${prefix}-thumbnail`
    };

    return names;
  };
  definePageMeta({
    // pageTransition: { name: 'page', mode: 'out-in' } 適宜ページのトランジションつけた方がいいのかも
  });
</script>

<style scoped>
  .view-transition {
    view-transition-name: var(--transition-name);
  }
  .heading {
    view-transition-name: heading;
  }
  .title {
    view-transition-name: var(--transition-title);
  }
  .thumbnail {
    view-transition-name: var(--transition-thumbnail);
    max-width: 100%;
  }
</style>

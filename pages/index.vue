<template>
  <div>
    <h1>indexxxxx</h1>
    <ContentDoc />
    <pre>{{ data }}</pre>
  </div>
</template>

<script setup>
  const { data } = await useAsyncData('data', () => queryContent('/').find());
</script>

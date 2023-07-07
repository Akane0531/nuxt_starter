<template>
  <div>
    <h1>posts/index</h1>
    <ContentList path="/" v-slot="{ list }">
      <div v-for="article in list" :key="article._path">
        <h2>{{ article.title }}</h2>
        <p>{{ article.description }}</p>
      </div>
    </ContentList>
  </div>
</template>

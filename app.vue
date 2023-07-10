<template>
  <NuxtPage />
</template>
<script setup></script>

<style>
  ::view-transition-group(*) {
    animation-duration: 1s;
  }
  .page-enter-active,
  .page-leave-active {
    transition: all 1s;
  }
  .page-enter-from,
  .page-leave-to {
    opacity: 0;
    filter: blur(1rem);
    transform: translateY(80px);
  }
</style>

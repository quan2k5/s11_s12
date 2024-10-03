<script setup>
import { onBeforeUnmount, onUnmounted } from 'vue';

onUnmounted(() => {
  console.log('onUnmounted');
});

onBeforeUnmount(() => {
  console.log('onBeforeUnmount');
});
</script>

<template>
  <div>
    component con
  </div>
</template>

<style scoped>
</style>

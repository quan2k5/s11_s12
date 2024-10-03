<script setup>
import { onUpdated } from 'vue';
const props = defineProps(['age']);
onUpdated(() => {
  alert('age đã thay đổi');
});
</script>

<template>
  <div>
  </div>
</template>

<style scoped>
</style>

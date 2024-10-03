<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
const count = ref(0);
onMounted(() => {
   setInterval(() => {
    count.value++;
  }, 1000);
});

</script>

<template>
  <div>
    <div>Ứng dụng đếm số</div>
    <div>Count: {{ count }}</div>
  </div>
</template>

<style scoped>
</style>

<template>
  <div>
    <p>Chiều rộng cửa sổ: {{ windowWidth }}px</p>
    <p>Màn hình khi resize còn {{ windowWidth }}px</p>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
const windowWidth = ref(window.innerWidth);
const updateWindowWidth = () => {
  windowWidth.value = window.innerWidth;
};
onMounted(() => {
  window.addEventListener('resize', updateWindowWidth);
});

onUnmounted(() => {
  window.removeEventListener('resize', updateWindowWidth);
});
</script>
<style scoped>

</style>

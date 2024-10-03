<script setup>
import { ref, onMounted, onUnmounted,onUpdated } from 'vue';
const emits=defineEmits(['checkad']);
const currentTime = ref(new Date().toLocaleTimeString());
let time;
onMounted(() => {
  time = setInterval(() => {
    currentTime.value = new Date().toLocaleTimeString();
  }, 1000);
});
onUpdated(() => {
    emits('checkad',currentTime.value)
})

onUnmounted(() => {
    emits('checkad',currentTime.value)
  clearInterval(time);
});
</script>
<template>
  <div>
    <h3>Thời gian hiện tại:</h3>
    <p>{{ currentTime }}</p>
  </div>
</template>


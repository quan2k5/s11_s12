<template>
  <div>
    <input v-model="input1" placeholder="Nhập giá trị"/>
  </div>
</template>
<script setup>
import { ref, watch } from 'vue';
const input1 = ref('');
watch(input1, (newValue) => {
  console.log(`Giá trị thay đổi từ "${input1.value.slice(0, -1)}" thành "${newValue}"`);
});
</script>
<style scoped>
</style>

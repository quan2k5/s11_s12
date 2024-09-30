<template>
  <div>
    <input type="number" v-model="number" placeholder="Enter a number" />
    <p>Current number: {{ number }}</p>
    <p>Square of the number: {{ squaredNumber }}</p>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue'
const number = ref(0)
const squaredNumber = computed(() => number.value * number.value)
watch(number, (newValue) => {
  console.log(`gia tri thay doi thanh ${newValue}`)
})
</script>

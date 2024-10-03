<template>
  <div>
    <p>Age: {{ age }}</p>
    <p>Company: {{ company }}</p>
    <button @click="randomizeAge">Random</button>
  </div>
</template>
<script setup>
import { ref ,onUpdated } from 'vue';
const age = ref(1);
const companies = ["Rikkei Academy", "Rikkei Education", "Rikkei Fukuoka"]; 
const company = ref(companies[0]); 
onUpdated(() => {
    company.value = companies[age.value % companies.length]; 
})
const randomizeAge = () => {
  age.value = Math.floor(Math.random() * 10) + 1; 
};
</script>
<style scoped>
</style>

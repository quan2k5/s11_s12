<script setup>
import {ref} from 'vue'
const isShow=ref(true);
const handleClick=()=>{
  isShow.value=!isShow.value;
}
</script>
<template>
  <div>
    <div v-show="isShow">Rikkei Education</div>
    <button v-on:click="handleClick">nhấn</button>    
  </div>
</template>
<style scoped>
</style>

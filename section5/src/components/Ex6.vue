<script setup>
import {ref} from 'vue'
const arr=ref([5,10,23,595,45,67,18,12]);
arr.value=arr.value.filter((e)=>{
    return e%2==0;
})
</script>
<template>
    <div>
      <span :key="number" v-for="number in arr">
      {{ number }}
    </span>
    </div>
</template>
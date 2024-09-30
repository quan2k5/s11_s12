<script setup>
import {ref} from 'vue'
const arr=ref([1,2,3,4,5,6,7,8,9,10]);
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
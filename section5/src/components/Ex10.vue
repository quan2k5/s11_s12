<script setup>
import {ref} from 'vue'
const arr=ref([]);
const handleRandom=()=>{
   arr.value.push(Math.floor(Math.random() * 10000));
}
</script>
<template>
    <div>
       <button @click="handleRandom">Random Number</button>
       <div>{{arr}}</div>
    </div>
</template>
<style scoped>
</style>

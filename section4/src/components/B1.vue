<script setup>
import {ref,watch} from 'vue'
const count=ref(0)
const increase=()=>{
  count.value++;
}
</script>
<template>
    <div>
        <button @click="increase">Click</button>
        <div>{{count}}</div>
    </div>
</template>
<style scoped>
</style>

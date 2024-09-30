<script setup>
import {ref,watch} from 'vue'
const width=ref(10);
const height=ref(20);
const handleClick=()=>{
    width.value+=10;
}
</script>
<template>
    <div>
        <button @click="handleClick">Click</button>
        <div>Diện tích: {{width*height}}</div>
    </div>
</template>
<style scoped>
</style>

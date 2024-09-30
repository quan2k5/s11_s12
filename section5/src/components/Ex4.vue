<script setup>
import {ref} from 'vue'
const isVisible=ref(false);
const handleAppear=()=>{
  isVisible.value=true;
}
const handleDisAppear=()=>{
  isVisible.value=false;
}
</script>
<template>
    <div>
        <button @click="handleAppear">Hiển thị</button>
        <button @click="handleDisAppear">Ân</button>
        <div>Thông báo:welcome to rikkei education</div>
    </div>
</template>
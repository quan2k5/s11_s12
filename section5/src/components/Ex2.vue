<script setup>
import {ref} from 'vue'
const isShow=ref(false);
const handleClick=()=>{
  isShow.value=!isShow.value;
}
</script>
<template>
    <div>
        <button @click="handleClick">{{isShow?"hiện":"ẩn"}}</button>
    </div>
</template>
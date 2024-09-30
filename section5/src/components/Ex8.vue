<script setup>
import {ref} from 'vue'
const arr=ref([2,9,1,5,6]);
const handleIncrease=()=>{
    arr.value.sort((a, b) => a - b);
}
const handleDecrease =() => {
    arr.value.sort((a, b) => b - a);
};
</script>
<template>
    <div>
        <button @click="handleIncrease">tăng</button>
         <button @click="handleDecrease">giảm</button>
         <br>
        <li :key="index" v-for="(number,index) in arr">{{number}}</li>  
    </div>
</template>
<style scoped>
</style>

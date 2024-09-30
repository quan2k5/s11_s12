<script setup>
import {ref} from 'vue'
const activeIndex=ref(1);
const handleClick=(number)=>{
    activeIndex.value=number;
}
</script>
<template>
    <div>
        <button v-bind:class="{active:activeIndex===1}" @click="handleClick(1)">Button 1</button>
        <button  v-bind:class="{active:activeIndex===2}" @click="handleClick(2)">Button 2</button>
        <button  v-bind:class="{active:activeIndex===3}" @click="handleClick(3)">Button 3</button>
    </div>
</template>
<style scoped>
.active{
    background-color: red;
    color:white;
}
</style>

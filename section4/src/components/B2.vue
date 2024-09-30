<script setup>
import {reactive} from 'vue'
const obj=reactive({
    company:"rikkei academy",
    age:2,
})
const handleClick=()=>{
    obj.company='rikkei education'
    obj.age=1
}
</script>
<template>
    <div>
        <button @click="handleClick">Click</button>
        <div>
            <div>company:{{obj.company}}</div>
            <div>age:{{obj.age}}</div>
        </div>
       
    </div>
</template>
<style scoped>
</style>

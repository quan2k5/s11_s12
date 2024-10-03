<script setup>
import {onUpdated,ref} from'vue';
const count=ref(0);
const handleClick=()=>{
    count.value++;
}
onUpdated(()=>{
    console.log('dữ liệu thay đổi');
    
})
</script>
<template>
    <div>
        <div>{{count}}</div>
        <button @click="handleClick">ấn</button>
    </div>
</template>
<style scoped>

</style>
<script setup>
import {onMounted,ref,onUpdated} from'vue';
const count=ref(0);
const increament=()=>{
    count.value++;
}
onUpdated(()=>{
    document.title=count.value;
})
</script>
<template>
    <div>
        <div>{{count}}</div>
        <button @click="increament">ấn</button>
    </div>
</template>
<style scoped>

</style>
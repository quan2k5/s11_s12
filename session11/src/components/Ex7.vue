<script setup>
import {onMounted,ref,onUpdated} from'vue';
const str=ref('');
onUpdated(()=>{
    document.title=str.value;
})
</script>
<template>
    <div>
        <input type="text" v-model="str">
    </div>
</template>
<style scoped>

</style>
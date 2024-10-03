<script setup>
import {onMounted,ref} from'vue';
import ex4Children from './Ex4Children.vue'
const age=ref(0);
const increaseAge=()=>{
    age.value++;
}
</script>
<template>
    <div>
        defffvfvfv
        <ex-4-children :age='age'></ex-4-children>
        <div>{{age}}</div>
        <button @click="increaseAge">ấn</button>
    </div>
</template>
<style scoped>

</style>
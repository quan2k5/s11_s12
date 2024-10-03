<script setup>
import {onMounted,ref} from'vue';
import ex5Children from './Ex5Children.vue'
const toggle=ref(true);
const handleClick=()=>{
    toggle.value=!toggle.value;
}
</script>
<template>
    <div>
        <ex-5-children v-if="toggle"></ex-5-children>
        <button @click='handleClick'>Toggle</button>
    </div>
</template>
<style scoped>

</style>